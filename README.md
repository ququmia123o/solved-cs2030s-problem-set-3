Download Link: https://assignmentchef.com/product/solved-cs2030s-problem-set-3
<br>
<ol>

 <li>Given the following interfaces.</li>

</ol>

interface Shape { double getArea();

}

interface Printable { void print();

}

<ul>

 <li>Suppose class Circle implements both interfaces above. Given the following program fragment,</li>

</ul>

Circle c = new Circle(new Point(0,0), 10);

Shape s = c;

Printable p = c;

Are the following statements allowed? Why do you think Java does not allow some of the following statements?

<ol>

 <li>print();</li>

 <li>print();</li>

</ol>

<ul>

 <li>getArea();iv. p.getArea();</li>

</ul>

<ul>

 <li>Someone proposes to re-implement Shape and Printable as abstract classes instead? Would statements (i) to (iv) be allowed?</li>

 <li>Now let’s define another interface PrintableShape as</li>

</ul>

public interface PrintableShape extends Printable, Shape {

}

and let class Circle implement PrintableShape instead. Would statements (i) to (iv) be allowed now? Can an interface inherit from multiple parent interfaces?

<ol start="2">

 <li>Suppose Java allows a class to inherit from multple parent classes. Give a concrete example why this could be problematic.</li>

</ol>

On the other hand, Java does allow classes to implement multiple interfaces. Explain why this isn’t problematic.

<ol start="3">

 <li>Consider the following classes: FormattedText that adds formatting information to the text. We call toggleUnderline() to add or remove underlines from the text. A PlainText is a FormattedText that is always NOT underlined.</li>

</ol>

class FormattedText { private final String text; private final boolean isUnderlined;

FormattedText(String text) { this.text = text; this.isUnderlined = false;

}

/*

* Overloaded constructor, but made private to prevent * clients from calling it directly.

*/ private FormattedText(String text, boolean isUnderlined) { this.text = text;

this.isUnderlined = isUnderlined;

}

FormattedText toggleUnderline() { return new FormattedText(this.text, !this.isUnderlined);

}

@Override public String toString() { if (this.isUnderlined) { return this.text + “(underlined)”;

} else {

return this.text;

}

}

}

class PlainText extends FormattedText {

PlainText(String text) { super(text); // text is NOT underlined

}

@Override

PlainText toggleUnderline() { return this;

}

}

Does the above violate Liskov Substitution Principle? Explain.

<ol start="4">

 <li>Consider the following program.</li>

</ol>

class A { int x;

A(int x) { this.x = x;

}

<ul>

 <li>method() {return new A(x);</li>

</ul>

}

}

class B extends A {

B(int x) {

super(x);

}

@Override

<ul>

 <li>method() {return new B(x);</li>

</ul>

}

}

Does it compile? What happens if we swap the entire definitions of method() between class A and class B? Does it compile now? Give reasons for your observations.