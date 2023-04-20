# Lab-8_202001140
# Name - Dhruv Baraiya
# ID - 202001140

1. Create a new Eclipse project, and within the project create a package.
2. Create a class for a Boa. Here’s the code you can use (you may copy/paste):
3. Follow the instructions in the JUnit tutorial in the section “Creating a JUnit Test Case in
Eclipse”. You’ll be creating a test case for the class Boa. When you’re asked to select
test method stubs, select both isHealthy() and fitsInCage(int).

![1](https://user-images.githubusercontent.com/124247747/233319495-8f1a9031-0f15-4150-aa3c-2485be4ac778.PNG)

## 1. Creating a new Eclipse project, package and defining the class
![M1](https://user-images.githubusercontent.com/124247747/233320408-022ceb28-80b0-4e55-b41d-e1b25a5af8cb.PNG)


### 2. Test method to test the behaviour of the Boa class : 
```
import org.junit.Assert;
import org.junit.Test;
public class BoaTest {

  @Test
  public void testIsHealthy() {
    Boa healthyBoa = new Boa("Lucy", 8, "granola bars");
    Assert.assertTrue(healthyBoa.isHealthy());
    
    Boa sickBoa = new Boa("Sneaky", 6, "mice");
    Assert.assertFalse(sickBoa.isHealthy());
  }

  @Test
  public void testFitsInCage() {
    Boa smallBoa = new Boa("Tiny", 2, "rats");
    Assert.assertTrue(smallBoa.fitsInCage(5));
    Assert.assertFalse(smallBoa.fitsInCage(1));

    Boa largeBoa = new Boa("Goliath", 20, "chicken");
    Assert.assertTrue(largeBoa.fitsInCage(25));
    Assert.assertFalse(largeBoa.fitsInCage(10));
  }
}
```
![M2](https://user-images.githubusercontent.com/124247747/233320524-ee95b415-223c-4f59-bc02-c7e78da88ef2.PNG)


</br>

### 3. Modified setUp() method in the BoaTest class : 
```
public class BoaTest {
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    // write test methods here
}
```
![M3](https://user-images.githubusercontent.com/124247747/233320672-3ae81a1b-2fe0-4df8-8488-bf8b7f801d99.PNG)


</br>

### 4. Modified testIsHealthy() method in the BoaTest class : 
```
@Test
public void testIsHealthy() {
    // check that jen is not healthy
    assertFalse(jen.isHealthy());
    
    // check that ken is healthy
    assertTrue(ken.isHealthy());
}
```
</br>

### 5. Modified testFitsInCage() method in the BoaTest class : 
```
@Test
public void testFitsInCage() {
    // Test for jen
    assertFalse(jen.fitsInCage(1)); // cage length is less than length of boa
    assertTrue(jen.fitsInCage(2)); // cage length is equal to length of boa
    assertTrue(jen.fitsInCage(3)); // cage length is greater than length of boa

    // Test for ken
    assertFalse(ken.fitsInCage(2)); // cage length is less than length of boa
    assertTrue(ken.fitsInCage(3)); // cage length is equal to length of boa
    assertTrue(ken.fitsInCage(4)); // cage length is greater than length of boa
}
```
</br>

### 6. Running test cases

![M4](https://user-images.githubusercontent.com/124247747/233320793-14c0898b-a39f-4655-b4d2-90fb78d24917.PNG)


### 7. Here's the modified Boa class with the new lengthInInches() method:
```
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;

    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }

    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }

    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }

    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}
```
### Here's an example of a new test case in the BoaTest class that tests the lengthInInches() method:
```
import static org.junit.Assert.assertEquals;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }

    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
```
This new test case checks that the lengthInInches() method returns the expected value when called on each of the Boa objects created in the setUp() method. It uses the assertEquals() method to compare the expected value to the actual value returned by the lengthInInches() method. The @Test annotation indicates that this is a test method that should be run by JUnit.
</br>
