package assignments;

import java.io.File;
import java.util.Scanner;
import java.io.FileNotFoundException;

public class textfile2DArray {

	private static Scanner scanner;

	public static void main (String[] args) {
		
		// creating a  2 dimensional array
		char[] array;
		char[][] multiArray = new char [20] [45];
		String output = "";
		 
		// this will bring the file up with text
		String file = readFile("Array.txt");
		array = file.toCharArray();
		
		// filling the empty spaces with "@" symbol
		for (int row = 0; row < multiArray.length - 1; row++) {
			for (int col = 0; col < multiArray[row].length - 1; col++) {
				multiArray[row][col] = '@';
			}
		}
		// looping for the rows
		int count = 0;
		for (int row = 0; row < multiArray.length - 2; row ++) {
			for (int col = 0; col < multiArray[row].length - 2; col++) {
				if (count == array.length) {
					break;
				}
				
				multiArray[row][col] = array[count];
				count++;			}
		}
		// looping for the columns
		for (int col = 0; col < multiArray[0].length - 3; col ++) {
			for (int row = 0; row < multiArray.length - 3; row++) {
				output = Character.toString(multiArray[row][col]);
				System.out.print(output);
			}
			// displays output in the 2d Array
				System.out.println(output);
		}
	}	
	
		public static String readFile(String file) {
			
			String text = "";
			try { 
				scanner = new Scanner(new File(file));
				
			while (scanner.hasNext()) {
				text = text + scanner.nextLine() + "";
			}	
		} 
			catch (FileNotFoundException f) {
				System.out.println("file could not be found, please find the correct file");
			}
			
			return text;
	}
}	
