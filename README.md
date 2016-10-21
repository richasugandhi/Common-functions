# Common-functions


function insert($data){	
        $this->db->insert($this->data, $data);
        return $this->db->insert_id();
    }
    
 function update($data, $where){	
        $this->db->update($this->data, $data, $where);
        return $this->get($where);
    }
    
    function delete($where){
    	$this->db->delete($this->data, $where); 
    }
    
    function get($where = array(), $limit = null, $offset = null) {
        $new_where = array();
        foreach( array_keys($where) as $key){
                $new_where['client.'.$key] = $where[$key];
        }
        $where = $new_where;
        $this->db->select($this->select, false);
        $query = $this->db->get_where($this->table, $where, $limit, $offset)->result_array();
	return $query;
    }
