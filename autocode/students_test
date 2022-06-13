package coverage

import (
	"os"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

//testing Len function of People type
func TestPeople_Len(t *testing.T) {
	person1 := Person{}
	person2 := Person{}
	
	p := People{}
	p = append(p, person1)
	p = append(p, person2)

	if p.Len() != 2 {
		t.Errorf("the expected length is 3, but actual %d", p.Len())
	}
}

//testing Less function of People type
func TestPeople_Less(t *testing.T) {
	now := time.Now();
	fName := "Maxxx"
	person1 := Person{firstName: fName, lastName: "Gor", birthDay: now}
	person2 := Person{firstName: "Vasya", lastName: "Gorn", birthDay: now.Add(-24 * time.Hour)}
	
	p := People{}
	p = append(p, person1)
	p = append(p, person2)

	if !p.Less(0,1) {
		t.Errorf("birthDay of first person %s should be more than second person %s", p[0].birthDay, p[1].birthDay)
	}

	p[1].birthDay = now
	if !p.Less(0,1) {
		t.Errorf("firstName of first person %s should be less than second person %s", p[0].firstName, p[1].firstName)
	}

	p[1].firstName = fName
	if !p.Less(0,1) {
		t.Errorf("lastName of first person %s should be less than second person %s", p[0].lastName, p[1].lastName)
	}
}

//testing Swap function of People type
func TestPeople_Swap(t *testing.T) {
	person1 := Person{firstName: "Max", lastName: "Gor", birthDay: time.Now()}
	person2 := Person{firstName: "Vasya", lastName: "Gorn", birthDay: time.Now().Add(-24 * time.Hour)}
	
	p := People{}
	p = append(p, person1)
	p = append(p, person2)

	p.Swap(0,1)

	if p[0] != person2 {
		t.Errorf("the expected first element should be second person %s", person2.firstName)
	}
}

///////////////////////////////////////////////////////////////////////////////////////////////////////

//testing Matrix structure
func TestMatrix_New(t *testing.T) {
	m, _ := New("1 2\n5 5 5")
	if m != nil {
		t.Errorf("when create new Matrix structure number of words  should be the same for each rows of the string")
	}
	m, _ = New("aaa aaaa\nbbb bbb")
	if m != nil {
		t.Errorf("Matrix structure should contain only numbers (int)")
	}
	m, _ = New("1 2\n5 3")
	if m == nil {
		t.Errorf("Matrix structure is not created, please check the code")
	}
}

//testing Matrix structure functions Rows and Cols
func TestMatrix_Rows(t *testing.T) {
	m, _ := New("1 2\n3 4")
	r := m.Rows()
	if r[1][0] != 3 {
		t.Errorf("when executing Matrix.Rows function we expected 3 on position [1][0] but, get %d", r[1][0])
	}

	c := m.Cols()
	if c[1][0] != 2 {
		t.Errorf("when executing Matrix.Cols function we expected 2 on position [0][1] but, get %d", r[1][0])
	}
}

//testing Matrix structure function Set
func TestMatrix_Set(t *testing.T) {
	m, _ := New("1 2\n3 4")
	
	isSet := m.Set(3, 0, 5)
	if isSet {
		t.Errorf("out of range when use function Matrix.Set")
	}
	
	isSet = m.Set(0, 0, 5)
	if !isSet {
		t.Errorf("expected true when use function Matrix.Set")
	}

	r :=m.Rows();
	if r[0][0] != 5 {
		t.Errorf("when use Matrix.Set function expected 5 on [0][0] position, but get %d", r[0][0])
	}
}