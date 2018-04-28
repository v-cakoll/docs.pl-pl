Za pomocą opartego na znakach indeksowanie z <xref:System.Text.StringBuilder.Chars%2A> właściwość może być bardzo wolno w następujących warunkach:

- <xref:System.Text.StringBuilder> Wystąpienia jest duży (na przykład składa się z kilku dziesiątki tysięcy znaków).
- <xref:System.Text.StringBuilder> Jest "ociężale". Oznacza to, takich jak powtarzane wywołania metod <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> automatycznie zostały rozszerzone obiektu <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> właściwości i przydzielone fragmentów nowej pamięci do niego.

Wydajność jest znacznemu obniżeniu, ponieważ dostęp do każdego znaku przeprowadzi całe połączonej listy fragmentów, aby znaleźć poprawne buforu indeksu w.

> [!NOTE]
>  Nawet w przypadku dużego "ociężale" <xref:System.Text.StringBuilder> obiekt, za pomocą <xref:System.Text.StringBuilder.Chars%2A> właściwość opartego na indeksie dostępu do jednej lub kilku małych znaków ma negatywny wpływ na wydajność nieznaczny; zazwyczaj jest **0(n)** operacji. Wpływ na wydajność znaczących występuje podczas wykonywania iteracji w znaki <xref:System.Text.StringBuilder> obiektu, który jest **O(n^2)** operacji. 

Jeśli wystąpią problemy z wydajnością, gdy za pomocą opartego na znakach indeksowanie z <xref:System.Text.StringBuilder> obiekty, można użyć dowolnego z następujących rozwiązań:

- Konwertuj <xref:System.Text.StringBuilder> wystąpienie do <xref:System.String> przez wywołanie metody <xref:System.Text.StringBuilder.ToString%2A> metody, dostęp do znaków w ciągu.

- Kopiuj zawartość istniejącej <xref:System.Text.StringBuilder> obiektu na nowy wstępnie o rozmiarze <xref:System.Text.StringBuilder> obiektu. Zwiększa wydajność, ponieważ nowy <xref:System.Text.StringBuilder> obiekt nie jest ociężale. Na przykład:

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- Wartość początkowa pojemność <xref:System.Text.StringBuilder> obiektu wartość jest równa około maksymalnego rozmiaru oczekiwany przez wywołanie metody <xref:System.Text.StringBuilder.%23ctor(System.Int32)> konstruktora. Należy pamiętać, że to przydziela cały blok pamięci, nawet jeśli <xref:System.Text.StringBuilder> rzadko osiągnie maksymalną pojemność.
