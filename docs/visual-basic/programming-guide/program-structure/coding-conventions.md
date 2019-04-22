---
title: Visual Basic — Konwencje kodowania
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f73648888b28c349104a70e78c29eb208d438b78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814565"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic — Konwencje kodowania
Microsoft rozwija przykłady i dokumentację, która jest zgodna z wytycznymi w tym temacie. Wykonanie tych samych konwencji kodowania możesz osiągnąć następujące korzyści:  
  
-   Twój kod będzie miał jednolity wygląd, tak aby czytelnicy mogli lepiej skupić się na treści, a nie na układzie.  
  
-   Czytniki rozumieją Twój kod lepiej szybko, ponieważ mogą robić więjsze założenia na podstawie poprzednich doświadczeń.  
  
-   Można skopiować, zmieniać i utrzymywać kod, aby łatwiej.  
  
-   Uzyskujesz pewność, że Twój kod wykazuje,, "Najważniejsze wskazówki" dla języka Visual Basic.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
  
-   Aby uzyskać informacje o zasadach nazywania, zobacz [wytyczne dotyczące nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) tematu.  
  
-   Nie należy używać "Mój" lub "Mój" jako część nazwy zmiennej. Praktyka ta tworzy omyłkowe `My` obiektów.  
  
-   Nie trzeba zmieniać nazwy obiektów w automatycznie wygenerowany kod, aby je dopasować do wytycznych.  
  
## <a name="layout-conventions"></a>Konwencje układu  
  
-   Wstaw tabulatory jako spacje i Użyj inteligentnego wcięcia z czterokrotnym wcięciem.  
  
-   Użyj **formatowania kodu automatyczne formatowanie kodu** Aby sformatować kod w edytorze kodu. Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstów, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Użyj tylko jednej instrukcji na wiersz. Nie używaj znaku separatora wierszy programu Visual Basic (:).  
  
-   Należy unikać znaku kontynuacji wiersza jawne "_" na rzecz niejawnej kontynuacji wiersza wszędzie tam, gdzie pozwala to język.  
  
-   Użyj tylko jednej deklaracji na wiersz.  
  
-   Jeśli **formatowania kodu automatyczne formatowanie kodu** nie formatuje wierszy kontynuacji automatycznie, ręcznie Utwórz wcięcia kontynuacji wierszy na jeden tabulator. Jednak zawsze wyrównuj do lewej elementy na liście.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Dodaj co najmniej jeden pusty wiersz między definicje metod i właściwości.  
  
## <a name="commenting-conventions"></a>Konwencje komentowania  
  
-   Umieść komentarze w osobnym wierszu zamiast na końcu wiersza kodu.  
  
-   Rozpocznij tekst komentarza wielką literą i tekst komentarza zakończenia kropką.  
  
-   Wstaw jedną spację między ogranicznik komentarza (') i tekst komentarza.  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
-   Nie otaczaj komentarzy sformatowanymi blokami ani gwiazdkami.  
  
## <a name="program-structure"></a>Struktura programu  
  
-   Kiedy używasz `Main` metody, użyj domyślnego konstruktora dla nowych aplikacji konsoli, a następnie użyj `My` dla argumentów wiersza poleceń.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Wytyczne dotyczące języka  
  
### <a name="string-data-type"></a>Typ danych ciągu  
  
-   Do łączenia ciągów, użyj handlowe "i" (&).  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
-   Aby dołączyć ciągi w pętli, należy użyć <xref:System.Text.StringBuilder> obiektu.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Obniżone Delegaty w procedurach obsługi zdarzeń  
 Nie kwalifikuj jawnie argumentów (obiekt i EventArgs) do obsługi zdarzeń. Jeśli nie używasz argumentów zdarzeń, które są przekazywane do zdarzenia (na przykład nadawcy jako obiektu, e jako EventArg), użyj swobodnych delegatów i Opuść argumenty zdarzenia w kodzie:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>Typ danych bez znaku  
  
-   Użyj `Integer` zamiast niepodpisanych typów, z wyjątkiem sytuacji, gdy jest to konieczne.  
  
### <a name="arrays"></a>Tablice  
  
-   Użyj skróconej składni podczas inicjowania tablic w wierszu deklaracji. Na przykład użyj następującej składni.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     Nie należy używać następującej składni.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
-   Umieść oznaczenie tablicy na typie, a nie na zmiennej. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     Nie należy używać następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
-   Do deklarowania i inicjowania tablic typów podstawowych danych, należy użyć składni {}. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     Nie należy używać następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>Korzystanie ze słowem kluczowym  
 Wprowadzając szereg wywołań do jednego obiektu, należy wziąć pod uwagę przy użyciu `With` — słowo kluczowe:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Użyj Try... CATCH i przy użyciu instrukcji, korzystając z obsługi wyjątków  
 Nie używaj `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Użyj słowa kluczowego IsNot  
 Użyj `IsNot` słowa kluczowego zamiast `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New — słowo kluczowe  
  
-   Użyj krótkiego tworzenia wystąpienia. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     Poprzedni wiersz jest równoważny następującemu wyrażeniu:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
-   Użyj inicjatorów obiektów dla nowych obiektów, a nie konstruktora bez parametrów:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Obsługa zdarzeń  
  
-   Użyj `Handles` zamiast `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
-   Użyj `AddressOf`i nie tworzyć wystąpienia pełnomocnika jawnie:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
-   Podczas definiowania zdarzenia, użyj skróconej składni i zezwolić kompilatorowi na zdefiniowanie delegata:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
-   Nie Weryfikuj, czy zdarzenie jest `Nothing` (null) przed wywołaniem `RaiseEvent` metody. `RaiseEvent` sprawdza, czy `Nothing` przed zzdarzenia.  
  
### <a name="using-shared-members"></a>Używanie udostępnionych elementów członkowskich  
 Wywołaj `Shared` elementów członkowskich przy użyciu nazwy klasy, nie ze zmiennej wystąpienia.  
  
### <a name="use-xml-literals"></a>Używanie literałów XML  
 Literały XML upraszczają najbardziej typowe zadania, które można napotkać podczas pracy z danymi XML (na przykład obciążenie, zapytań i przekształcania). Podczas pracy z danymi XML należy przestrzegać następujących wytycznych:  
  
-   Literały XML umożliwiają tworzenie dokumentów XML i fragmentów zamiast wywoływania interfejsów API XML bezpośrednio.  
  
-   Zaimportuj przestrzenie nazw XML na poziomie pliku lub projektu, aby skorzystać z optymalizacji wydajności w literałach XML.  
  
-   Właściwości osi XML umożliwiają dostęp do elementów i atrybutów w dokumencie XML.  
  
-   Użyj wyrażenia osadzone umożliwiają uwzględnienie wartości i tworzenie kodu XML na podstawie istniejących wartości, zamiast przy użyciu wywołań interfejsu API, takich jak `Add` metody:  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>Zapytania LINQ  
  
-   Użyj nazw opisowych dla zmiennych kwerendy:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
-   Zapewnij nazwy elementów w zapytaniu, aby upewnić się, że nazwy właściwości anonimowych typów są kapitalizowane poprawnie przy użyciu obudowy Pascal wielkość liter w wyrazie:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
-   Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłby niejednoznaczne. Na przykład, jeśli zapytanie zwraca klienta nazwa i identyfikator zamówienia, zmień je zamiast pozostawiania je jako `Name` i `ID` w wyniku:  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
-   Użyj wnioskowania o typie w deklaracji zmiennych kwerendy i zmiennych zakresu:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
-   Wyrównaj klauzule zapytania pod `From` instrukcji:  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
-   Użyj `Where` klauzule przed innymi klauzulami kwerend powoduje, że późniejsze klauzule kwerend działają na zestawie filtrowanych danych:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
-   Użyj `Join` klauzuli umożliwia jawne zdefiniowanie operacji join w przeciwieństwie `Where` klauzuli umożliwia niejawnie określenie operacji join:  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../standard/security/secure-coding-guidelines.md)
