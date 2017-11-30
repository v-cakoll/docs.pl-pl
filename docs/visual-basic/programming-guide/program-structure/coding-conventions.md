---
title: "Visual Basic — Konwencje kodowania"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: afea862fb8783da3e69fd9828e0ded67fb81b00e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic — Konwencje kodowania
Microsoft rozwija przykłady i dokumentację postępuj zgodnie z wytycznymi, w tym temacie. Po wykonaniu tej samej Konwencji kodowania mogą zyskać następujące korzyści:  
  
-   Kod będzie mieć spójny wygląd, tak aby czytników lepiej można skupić się na zawartości, nie układu.  
  
-   Czytniki poznać kod więcej szybko ponieważ mogą one ułatwić założenia doświadczenia w oparciu.  
  
-   Można skopiować, zmienianie i łatwiej Obsługa kodu.  
  
-   Pomoc, upewnij się, że kod pokazuje "najlepsze rozwiązania" w języku Visual Basic.  
  
## <a name="naming-conventions"></a>Konwencje nazewnictwa  
  
-   Informacje o wskazówki dotyczące nazewnictwa, zobacz [nazewnictwa wytyczne](../../../standard/design-guidelines/naming-guidelines.md) tematu.  
  
-   Nie używaj "Moje" lub "Moje" jako część nazwy zmiennej. Takie rozwiązanie tworzy pomylenia z `My` obiektów.  
  
-   Nie trzeba zmienić nazwy obiektów w automatycznie wygenerowany kod, aby je dopasować wytyczne.  
  
## <a name="layout-conventions"></a>Konwencje układu  
  
-   Wstaw jako spacje i użyj inteligentne tworzenia wcięć za pomocą czterech miejsca wcięcia.  
  
-   Użyj **automatycznego formatowania kodu (ponowne formatowanie) z** do ponownego formatowania kodu w edytorze kodu. Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstów, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Użyj tylko jednej instrukcji w jednym wierszu. Nie używaj znaku separatora linii Visual Basic (:).  
  
-   Unikaj używania znak kontynuacji wiersza jawne "_" na rzecz kontynuacji wiersza niejawne wszędzie tam, gdzie pozwala języka.  
  
-   Użyj tylko jedna deklaracja w wierszu.  
  
-   Jeśli **automatycznego formatowania kodu (ponowne formatowanie) z** nie Formatuj kontynuacji linie automatycznie, ręcznie wcięcie kontynuacji wierszy jednego tabulatora. Jednak zawsze lewej align elementów na liście.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Dodaj co najmniej jeden pusty wiersz między definicje metod i właściwości.  
  
## <a name="commenting-conventions"></a>Konwencje komentowania  
  
-   Wprowadzone komentarze w osobnym wierszu zamiast na końcu wiersza kodu.  
  
-   Uruchom tekst komentarza od wielkiej litery i tekst komentarza zakończenia kropką.  
  
-   Wstaw spację jednego między ogranicznik komentarza (') i tekst komentarza.  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Nie należy ująć komentarze sformatowany bloki gwiazdek.  
  
## <a name="program-structure"></a>Struktura programu  
  
-   Jeśli używasz `Main` metody konstrukcji domyślne dla nowych aplikacji konsoli i wykorzystaj `My` dla argumentów wiersza polecenia.  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Wytyczne dotyczące języka  
  
### <a name="string-data-type"></a>Typ danych ciągu  
  
-   Aby ciągów, należy użyć handlowego "i" (&).  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Aby dołączyć ciągów w pętli, należy użyć <xref:System.Text.StringBuilder> obiektu.  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Swobodna delegatów w obsłudze zdarzeń  
 Nie jawnie kwalifikują się argumentów (obiektu i EventArgs) do obsługi zdarzeń. Jeśli nie używasz argumenty zdarzenia, które są przekazywane do zdarzeń (na przykład nadawcy jako obiekt, e jako EventArgs), używać delegatów swobodna i Opuść argumenty zdarzeń w kodzie:  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>Typ danych bez znaku  
  
-   Użyj `Integer` zamiast typy bez znaku, z wyjątkiem przypadków, gdy jest to konieczne.  
  
### <a name="arrays"></a>Tablice  
  
-   Podczas inicjowania tablic w wierszu deklaracji, należy użyć składni krótki. Na przykład użyj następującej składni.  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Nie należy użyć następującej składni.  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   W typie, a nie na zmiennej, umieść oznaczeniem tablicy. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Nie należy użyć następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Po zadeklarowaniu i zainicjować tablice typów podstawowych danych, należy użyć składni {}. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Nie należy użyć następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Użyj ze słowem kluczowym  
 Po wprowadzeniu szereg wywołania do jednego obiektu, należy rozważyć użycie `With` — słowo kluczowe:  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Użyj Try... CATCH i przy użyciu instrukcji, korzystając z obsługą wyjątków  
 Nie używaj `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Użyj słowa kluczowego IsNot  
 Użyj `IsNot` słowa kluczowego zamiast `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New, słowo kluczowe  
  
-   Użyj wystąpienia krótki. Na przykład użyj następującej składni:  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     Poprzedni wiersz jest odpowiednikiem to:  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Inicjatory obiektów należy użyć dla nowych obiektów zamiast konstruktora bez parametrów:  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Obsługa zdarzeń  
  
-   Użyj `Handles` zamiast `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Użyj `AddressOf`, a nie wystąpienia delegat jawnie:  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Podczas definiowania zdarzenia należy użyć składni krótki i umożliwić kompilatora zdefiniuj delegata:  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Sprawdza, czy zdarzenie jest `Nothing` (null), przed wywołaniem `RaiseEvent` metody. `RaiseEvent`sprawdza, czy `Nothing` przed zgłasza zdarzenie.  
  
### <a name="using-shared-members"></a>Przy użyciu udostępniane elementy członkowskie  
 Wywołanie `Shared` elementów członkowskich za pomocą nazwy klasy, nie z zmienna wystąpienia.  
  
### <a name="use-xml-literals"></a>Używaj literałów XML  
 Literały XML uprościć najbardziej typowych zadań, które wystąpią podczas pracy z XML (na przykład, obciążenia, zapytań i przekształcenie). Podczas pracy z danymi XML, skorzystaj z następujących wskazówek:  
  
-   Literały XML umożliwia tworzenie dokumentów XML i fragmentów, zamiast bezpośredniego wywoływania interfejsów API XML.  
  
-   Importuj przestrzeni nazw XML na poziomie pliku lub projektu, aby skorzystać z optymalizacji wydajności dla literałów XML.  
  
-   Właściwości osi XML umożliwia dostęp do elementów i atrybutów w dokumencie XML.  
  
-   Użyj wyrażenia osadzone wartości mają zostać uwzględnione i utworzyć XML z istniejącymi wartościami zamiast przy użyciu interfejsu API, takich jak `Add` metody:  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>Zapytania LINQ  
  
-   Użyj łatwy do rozpoznania nazwy zmiennych zapytania:  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Nazwy elementów w zapytaniu, aby upewnić się, że nazwy właściwości typu anonimowego poprawnie kapitalizacji przy użyciu Pascal wielkości liter:  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłoby niejednoznaczne. Na przykład, jeśli zapytanie zwraca klienta nazwa i identyfikator zamówienia, zmień ich zamiast zostawiać je jako `Name` i `ID` w wyniku:  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Wnioskowanie o typie należy użyć w deklaracji zmiennych zakresu i zmiennych zapytania:  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Dopasuj klauzule zapytań w obszarze `From` instrukcji:  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Użyj `Where` klauzule przed innymi kwerendy w klauzulach sposób nowsze klauzule zapytań działać na odfiltrowanego zbioru danych:  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Użyj `Join` klauzuli, aby jawnie definiować operacji tworzenia sprzężenia zamiast `Where` klauzuli niejawnie określenie operacji tworzenia sprzężenia:  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../standard/security/secure-coding-guidelines.md)
