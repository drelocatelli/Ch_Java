# Connect.java

```
package database;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class Connect {

	private static Connection conn = null;
	
	private static String host, dbName, dbUser, dbPass;
	
	public static Connection getConnection() {
		host = "localhost";
		dbName = "dbname";
		dbUser = "root";
		dbPass = "password";

		
		if (conn == null) {
			try {
				String url = String.format("jdbc:mysql://%s:3306/%s", host, dbName);
				
				conn = DriverManager.getConnection(url, dbUser, dbPass);
			}
			catch (SQLException e) {
				
			}
		}
		return conn;
	}
	
	public static void closeConnection() {
		if (conn != null) {
			try {
				conn.close();
			} catch (SQLException e) {
				
			}
		}
	}
	
	public static void closeStatement(Statement st) {
		if (st != null) {
			try {
				st.close();
			} catch (SQLException e) {
				
			}
		}
	}

	public static void closeResultSet(ResultSet rs) {
		if (rs != null) {
			try {
				rs.close();
			} catch (SQLException e) {
				
			}
		}
	}
}
```

# Basic about return values
```
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import Database.*;

public void getConfig() {
		Connection conn = null;
		Statement st = null;
		ResultSet rs = null;
		
		try {
			
			conn = Connect.getConnection();
			st = conn.createStatement();
			rs = st.executeQuery("SELECT * FROM config");
			
			while(rs.next()) {
				title = rs.getString("title");
				version = rs.getString("version");
				login = rs.getString("login");
				password = rs.getString("senha");
				description = rs.getString("description");
			}
			
		}catch(SQLException e) {
			e.printStackTrace();
		}finally{
			Connect.closeResultSet(rs);
			Connect.closeStatement(st);
//			Connect.closeConnection();
		}
		
	}
```
