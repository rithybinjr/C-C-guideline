<pre>#include &lt;cstdio&gt;<br />#include &lt;iostream&gt;<br />using namespace std;<br /><br />class Rational {<br />    int _n = 0;<br />    int _d = 1;<br />public:<br />    Rational ( int numerator = 0, int denominator = 1 ) : _n(numerator), _d(denominator) {};<br />    Rational ( const Rational &amp; rhs ) : _n(rhs._n), _d(rhs._d) {}; // copy constructor<br />    ~Rational ();<br />    inline int numerator() const { return _n; };<br />    inline int denominator() const { return _d; };<br />    Rational &amp; operator = ( const Rational &amp; );<br />    Rational operator + ( const Rational &amp; ) const;<br />    Rational operator - ( const Rational &amp; ) const;<br />    Rational operator * ( const Rational &amp; ) const;<br />    Rational operator / ( const Rational &amp; ) const;<br />};<br /><br />Rational &amp; Rational::operator = ( const Rational &amp; rhs ) {<br />    if( this != &amp;rhs ) {<br />        _n = rhs.numerator();<br />        _d = rhs.denominator();<br />    }<br />    return *this;<br />}<br /><br />Rational Rational::operator + ( const Rational &amp; rhs ) const {<br />    return Rational((_n * rhs._d) + (_d * rhs._n), _d * rhs._d);<br />}<br /><br />Rational Rational::operator - ( const Rational &amp; rhs ) const {<br />    return Rational((_n * rhs._d) - (_d * rhs._n), _d * rhs._d);<br />}<br /><br />Rational Rational::operator * ( const Rational &amp; rhs ) const {<br />    return Rational(_n * rhs._n, _d * rhs._d);<br />}<br /><br />Rational Rational::operator / ( const Rational &amp; rhs ) const {<br />    return Rational(_n * rhs._d, _d * rhs._n);<br />}<br /><br />Rational::~Rational() {<br />    _n = 0; _d = 1;<br />}<br /><br />// useful for std::cout<br />std::ostream &amp; operator &lt;&lt; (std::ostream &amp; o, const Rational &amp; r) {<br />    return o &lt;&lt; r.numerator() &lt;&lt; '/' &lt;&lt; r.denominator();<br />}<br /><br />int main( int argc, char ** argv ) {<br />    <br />    Rational a = 7;       // 7/1<br />    cout &lt;&lt; "a is: " &lt;&lt; a &lt;&lt; endl;<br />    Rational b(5, 3);  // 5/3<br />    cout &lt;&lt; "b is: " &lt;&lt; b &lt;&lt; endl;<br />    Rational c = b;       // copy constructor<br />    cout &lt;&lt; "c is: " &lt;&lt; c &lt;&lt; endl;<br />    Rational d;          // default constructor<br />    cout &lt;&lt; "d is: " &lt;&lt; d &lt;&lt; endl;<br />    d = c;          // assignment operator<br />    cout &lt;&lt; "d is: " &lt;&lt; d &lt;&lt; endl;<br />    Rational &amp; e = d;  // reference<br />    d = e;          // assignment to self!<br />    cout &lt;&lt; "e is: " &lt;&lt; e &lt;&lt; endl;<br />    <br />    cout &lt;&lt; a &lt;&lt; " + " &lt;&lt; b &lt;&lt; " = " &lt;&lt; a + b &lt;&lt; endl;<br />    cout &lt;&lt; a &lt;&lt; " - " &lt;&lt; b &lt;&lt; " = " &lt;&lt; a - b &lt;&lt; endl;<br />    cout &lt;&lt; a &lt;&lt; " * " &lt;&lt; b &lt;&lt; " = " &lt;&lt; a * b &lt;&lt; endl;<br />    cout &lt;&lt; a &lt;&lt; " / " &lt;&lt; b &lt;&lt; " = " &lt;&lt; a / b &lt;&lt; endl;<br />    return 0;<br />}</pre>
