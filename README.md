import java.util.HashMap;

import java.util.LinkedList;

import java.util.List;

import java.util.Map;

import java.util.Scanner;
 
public class IncidentList

{
    
    private Map<Integer, List<Integer>> incidentList;
    
    private int numberOfVertices;
 
    public IncidentList(int numberOfVertices)
    
    {
        
        this.numberOfVertices = numberOfVertices;
        
        incidentList = new HashMap<Integer, List<Integer>>();
 
        for (int vertex = 1; vertex <= numberOfVertices; vertex++)
            
            incidentList.put(vertex, new LinkedList<Integer>());
    
    }
 
    public void setEdge(int sourcevertex, int destinationvertex, int edgeNumber)
    
    {
        
        List<Integer> slist = incidentList.get(sourcevertex);
        
        slist.add(edgeNumber);
        
        return;
    
    }
 
    public List<Integer> getEdge(int vertex)
    
    {
        
        return incidentList.get(vertex);
    
    }
 
    public void printIncidentList()
    
    {
        
        System.out.println("Vertex   EdgeNumber");
        
        for (int vertex = 1; vertex <= numberOfVertices; vertex++)
        
        {
            
            System.out.print(vertex + ":");
            
            List<Integer> edgeList = getEdge(vertex);
 
            for (int j = 1; ; j++)
            
            {
                
                if (j != edgeList.size())
                    
                    System.out.print(edgeList.get(j - 1) + "\t");
                
                else
                
                {
                    
                    System.out.print(edgeList.get(j - 1));
                    
                    break;
                
                }
            
            }
            
            System.out.println();
        
        }
    
    }
 
    public static void main(String... arg)
    
    {
        
        int numberOfVertices, numberOfEdges;
        
        int source, destination, edgeNumber;
        
        int edgeCount = 1;
 
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enter the number of vertices");
        
        numberOfVertices = scanner.nextInt();
 
        IncidentList incidentList = new IncidentList(numberOfVertices);
        
        System.out.println("Enter the number of edges");
        
        numberOfEdges = scanner.nextInt();
 
        System.out.println("Enter the edges format : <edgeNumber> <source> <destination>");
        
        while (edgeCount <= numberOfEdges)
        
        {
            
            edgeNumber = scanner.nextInt();
            
            source = scanner.nextInt();
            
            destination = scanner.nextInt();
            
            incidentList.setEdge(source, destination, edgeNumber);
            
            edgeCount++;
        
        }
 
        System.out.println("\nThe Incident List is ");
        
        incidentList.printIncidentList();
        
        scanner.close();
    
    }

}
