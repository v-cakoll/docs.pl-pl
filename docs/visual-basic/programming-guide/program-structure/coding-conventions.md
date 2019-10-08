---
title: Visual Basic — Konwencje kodowania
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 18c309e22cccfa5d835394996fc6974d95825b65
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003118"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic — Konwencje kodowania
Firma Microsoft opracowuje przykłady i dokumentację, które są zgodne z wytycznymi w tym temacie. Jeśli przestrzegasz tych samych konwencji kodowania, możesz uzyskać następujące korzyści:  
  
- Twój kod będzie miał spójny wygląd, dzięki czemu czytelnicy mogą lepiej skupić się na zawartości, a nie na układzie.  
  
- Czytelnicy mogą szybciej zrozumieć swój kod, ponieważ może to spowodować założenie założeń na podstawie poprzedniego środowiska.  
  
- Można łatwo kopiować, zmieniać i konserwować kod.  
  
- W celu zagwarantowania, że kod demonstruje "najlepsze rozwiązania" Visual Basic.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
  
- Aby uzyskać informacje na temat określania zasad nazewnictwa, zobacz temat Omówienie [nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) .  
  
- Nie należy używać "my" ani "my" jako części nazwy zmiennej. To rozwiązanie tworzy pomyłkę z obiektami `My`.  
  
- Nie trzeba zmieniać nazw obiektów w generowanym automatycznie kodzie, aby dopasować je do wytycznych.  
  
## <a name="layout-conventions"></a>Konwencje układu  
  
- Wstaw tabulatory jako spacje i używaj inteligentnych wcięć z czterema znakami odstępu.  
  
- Korzystaj **z** przeglądarki, aby ponownie formatować kod w edytorze kodu. Aby uzyskać więcej informacji, zobacz [Opcje, Edytor tekstu, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
- Używaj tylko jednej instrukcji w wierszu. Nie używaj znaku separatora wiersza Visual Basic (:).  
  
- Unikaj używania jawnego znaku kontynuacji wiersza "_" na rzecz niejawnej kontynuacji wiersza wszędzie tam, gdzie język ten zezwala.  
  
- Użyj tylko jednej deklaracji na wiersz.  
  
- Jeśli podczas tworzenia **listy (ponowne formatowanie) kodu** nie są automatycznie formatowane linie kontynuacji, ręcznie Zwiększ wcięcie wierszy kontynuacji o jeden tabulator. Jednak zawsze należy wyrównać elementy na liście.  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- Dodaj co najmniej jeden pusty wiersz między definicją metody i właściwości.  
  
## <a name="commenting-conventions"></a>Konwencje komentowania  
  
- Umieść komentarze w osobnym wierszu zamiast na końcu wiersza kodu.  
  
- Zacznij komentować tekst komentarza z wielką literą i Zakończ tekst komentarza z kropką.  
  
- Wstaw jedną spację między ogranicznikiem komentarza (') a tekstem komentarza.  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- Nie otaczaj komentarzy sformatowanymi blokami gwiazdek.  
  
## <a name="program-structure"></a>Struktura programu  
  
- Korzystając z metody `Main`, Użyj domyślnej konstrukcji dla nowych aplikacji konsolowych i użyj `My` dla argumentów wiersza polecenia.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Wytyczne dotyczące języka  
  
### <a name="string-data-type"></a>Typ danych ciągu  
  
- Użyj [interpolacji ciągów](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings) , aby połączyć krótkie ciągi, jak pokazano w poniższym kodzie.
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- Aby dołączyć ciągi w pętlach, użyj obiektu <xref:System.Text.StringBuilder>.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Elementy delegowane swobodne w obsłudze zdarzeń  
 Nie należy jawnie kwalifikować argumentów (Object i EventArgs) do programów obsługi zdarzeń. Jeśli nie używasz argumentów zdarzeń, które są przekazane do zdarzenia (na przykład nadawcy jako obiekt, e jako EventArgs), użyj swobodnych delegatów i pozostaw argumenty zdarzeń w kodzie:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>Typ danych bez znaku  
  
- Użyj `Integer`, a nie typów niepodpisanych, z wyjątkiem tego, gdzie są niezbędne.  
  
### <a name="arrays"></a>Tablice  
  
- Podczas inicjowania tablic w wierszu deklaracji należy użyć krótkiej składni. Na przykład użyj następującej składni.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     Nie należy używać następującej składni.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- Umieść oznaczenie tablicy na typie, a nie na zmiennej. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     Nie należy używać następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- Użyj składni {} podczas deklarowania i inicjowania tablic podstawowych typów danych. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     Nie należy używać następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>Używanie słowa kluczowego with  
 Podczas wykonywania serii wywołań do jednego obiektu Rozważ użycie słowa kluczowego `With`:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Użyj try... Instrukcje catch i Using w przypadku korzystania z obsługi wyjątków  
 Nie należy używać `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Użycie słowa kluczowego IsNot  
 Użyj słowa kluczowego `IsNot` zamiast `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New — słowo kluczowe  
  
- Użyj krótkiego tworzenia wystąpienia. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     Poprzedni wiersz jest równoważny z:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- Użyj inicjatorów obiektów dla nowych obiektów zamiast konstruktora bez parametrów:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Obsługa zdarzeń  
  
- Użyj `Handles`, a nie `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- Użyj `AddressOf` i nie określaj wystąpienia delegata jawnie:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- Podczas definiowania zdarzenia Użyj krótkiej składni i pozwól kompilatorowi definiować delegata:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- Nie sprawdzaj, czy przed wywołaniem metody `RaiseEvent` dla zdarzenia `Nothing` (null). `RaiseEvent` sprawdza, czy `Nothing` przed wyjęciem zdarzenia.  
  
### <a name="using-shared-members"></a>Korzystanie z udostępnionych elementów członkowskich  
 Wywołaj `Shared` członków przy użyciu nazwy klasy, a nie z zmiennej wystąpienia.  
  
### <a name="use-xml-literals"></a>Użyj literałów XML  
 Literały XML upraszczają Najczęstsze zadania, które można napotkać podczas pracy z XML (na przykład ładowania, wykonywania zapytań i przekształcania). Opracowując with XML, postępuj zgodnie z następującymi wskazówkami:  
  
- Za pomocą literałów XML można tworzyć dokumenty i fragmenty XML, zamiast bezpośrednio wywoływanie interfejsów API XML.  
  
- Zaimportuj przestrzenie nazw XML na poziomie pliku lub projektu, aby skorzystać z optymalizacji wydajności dla literałów XML.  
  
- Użyj właściwości osi XML, aby uzyskać dostęp do elementów i atrybutów w dokumencie XML.  
  
- Użyj osadzonych wyrażeń, aby dołączyć wartości i utworzyć XML z istniejących wartości zamiast używać wywołań interfejsu API, takich jak Metoda `Add`:  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>Zapytania LINQ  
  
- Użyj znaczących nazw dla zmiennych zapytania:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- Podaj nazwy dla elementów w zapytaniu, aby upewnić się, że nazwy właściwości typów anonimowych są prawidłowo pisane wielkimi literami przy użyciu wielkości liter w Pascalu:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłyby niejednoznaczne. Na przykład, jeśli zapytanie zwróci nazwę klienta i identyfikator zamówienia, zmień ich nazwy zamiast pozostawić je jako `Name` i `ID` w wyniku:  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- Użyj wnioskowania o typie w deklaracji zmiennych zapytania i zmiennych zakresu:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- Wyrównaj klauzule zapytania w instrukcji `From`:  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- Użyj klauzul `Where` przed innymi klauzulami zapytania, tak aby późniejsze klauzule zapytań działały na filtrowanym zestawie danych:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- Użyj klauzuli `Join` w celu jawnego zdefiniowania operacji JOIN zamiast używania klauzuli `Where` do niejawnie zdefiniowanej operacji JOIN:  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../standard/security/secure-coding-guidelines.md)
