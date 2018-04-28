### <a name="path-colon-checks-are-stricter"></a>Ścieżka kontroli dwukropka są bardziej restrykcyjne

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 Liczba zmian wprowadzono obsługuje ścieżek wcześniej nieobsługiwany (zarówno w długości i formatu). Sprawdza, czy składnia separatora (dwukropek) właściwy dysk wprowadzono więcej poprawne, które spowodowały po stronie blokuje niektóre kilka wybierz ścieżkę interfejsów API gdzie używane do się ścieżki identyfikatora URI.|
|Sugestia|Jeśli przekazywanie URI do odpowiednich interfejsów API, zmodyfikuj ciąg jako ścieżka.<ul><li>Ręcznie usuń system z adresów URL (np. Usuń <code>file://</code> z adresów URL)</li><li>Identyfikator URI do przekazania <xref:System.Uri> klasy i użycia <xref:System.Uri.LocalPath></li></ul>Alternatywnie można zrezygnować z nowego normalizacji ścieżka przez ustawienie <code>Switch.System.IO.UseLegacyPathHandling</code> przełącznika AppContext na wartość true.|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|

