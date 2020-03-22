---
title: Zdarzenia
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 666e138a747c480ef9e8b593f8c6233105fcdc93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400842"
---
# <a name="events-visual-basic"></a>Zdarzenia (Visual Basic)
Chociaż można wizualizować projekt programu Visual Studio jako serię procedur, które są wykonywane w sekwencji, w rzeczywistości większość programów jest sterowana zdarzeniami, co oznacza, że przepływ wykonania jest określany przez wystąpienia zewnętrzne zwane *zdarzeniami.*  
  
 Zdarzenie jest sygnałem informującym aplikację o wystąpieniu czegoś ważnego. Na przykład, gdy użytkownik kliknie formant w formularzu, formularz może podnieść `Click` zdarzenie i wywołać procedurę, która obsługuje zdarzenie. Zdarzenia umożliwiają również oddzielne zadania do komunikowania się. Powiedzmy, na przykład, że aplikacja wykonuje zadanie sortowania oddzielnie od aplikacji głównej. Jeśli użytkownik anuluje sortowanie, aplikacja może wysłać zdarzenie anuluj polecenie zatrzymania procesu sortowania.  
  
## <a name="event-terms-and-concepts"></a>Warunki i pojęcia dotyczące zdarzeń  
 W tej sekcji opisano terminy i pojęcia używane ze zdarzeniami w języku Visual Basic.  
  
### <a name="declaring-events"></a>Deklarowanie zdarzeń  
 Deklarujesz zdarzenia w klasach, strukturach, modułach `Event` i interfejsach przy użyciu słowa kluczowego, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Podnoszenie wydarzeń  
 Zdarzenie jest jak komunikat informujący, że wydarzyło się coś ważnego. Akt nadawanie wiadomości nazywa *się podniesienie* zdarzenia. W języku Visual Basic można `RaiseEvent` podnieść zdarzenia z instrukcją, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Zdarzenia muszą być wywoływane w zakresie klasy, modułu lub struktury, gdzie są one zadeklarowane. Na przykład klasa pochodna nie może podnieść zdarzeń dziedziczonych z klasy podstawowej.  
  
### <a name="event-senders"></a>Nadawcy zdarzeń  
 Każdy obiekt zdolny do wywoływania zdarzenia jest *nadawcą zdarzeń,* znanym również jako *źródło zdarzenia.* Formularze, formanty i obiekty zdefiniowane przez użytkownika są przykładami nadawców zdarzeń.  
  
### <a name="event-handlers"></a>Programy obsługi zdarzeń  
 Programy obsługi zdarzeń są *procedury,* które są wywoływane, gdy wystąpi odpowiednie zdarzenie. Można użyć dowolnego prawidłowego podprocedura z podpisem pasujące jako program obsługi zdarzeń. Nie można jednak użyć funkcji jako programu obsługi zdarzeń, ponieważ nie może zwrócić wartości do źródła zdarzeń.  
  
 Visual Basic używa standardowej konwencji nazewnictwa dla programów obsługi zdarzeń, która łączy nazwę nadawcy zdarzenia, podkreślenia i nazwę zdarzenia. Na przykład `Click` zdarzenie o nazwie `button1` przycisku `Sub button1_Click`będzie miało nazwę .  
  
> [!NOTE]
> Zaleca się użycie tej konwencji nazewnictwa podczas definiowania programów obsługi zdarzeń dla własnych zdarzeń, ale nie jest to wymagane; można użyć dowolnej prawidłowej nazwy podprocedury.  
  
## <a name="associating-events-with-event-handlers"></a>Kojarzenie zdarzeń z programami obsługi zdarzeń  
 Zanim program obsługi zdarzeń stanie się użyteczny, należy najpierw skojarzyć go ze zdarzeniem przy użyciu `Handles` instrukcji lub. `AddHandler`  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents i klauzuli uchwytów  
 Instrukcja `WithEvents` `Handles` i klauzula zapewniają deklaratywny sposób określania obsługi zdarzeń. Zdarzenie wywoływane przez obiekt `WithEvents` zadeklarowany za pomocą słowa kluczowego może być obsługiwane przez dowolną procedurę z instrukcją `Handles` dla tego zdarzenia, jak pokazano w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 Instrukcja `WithEvents` i `Handles` klauzula są często najlepszym wyborem dla programów obsługi zdarzeń, ponieważ składni deklaratywna, której używają, ułatwia obsługę zdarzeń do kodowania, odczytu i debugowania. Należy jednak pamiętać o następujących ograniczeniach `WithEvents` dotyczących stosowania zmiennych:  
  
- Nie można `WithEvents` użyć zmiennej jako zmiennej obiektu. Oznacza to, że nie `Object`można zadeklarować go jako — należy określić nazwę klasy podczas deklarowania zmiennej.  
  
- Ponieważ zdarzenia udostępnione nie są powiązane z `WithEvents` wystąpieniami klasy, nie można używać do deklaratywnego obchodzenia się ze zdarzeniami udostępnionymi. Podobnie nie można `WithEvents` używać `Handles` ani obsługiwać `Structure`zdarzeń z pliku . W obu przypadkach można `AddHandler` użyć instrukcji do obsługi tych zdarzeń.  
  
- Nie można tworzyć `WithEvents` tablic zmiennych.  
  
 `WithEvents`zmienne umożliwiają jeden program obsługi zdarzeń do obsługi jednego lub więcej rodzaju zdarzenia lub jeden lub więcej programów obsługi zdarzeń do obsługi tego samego rodzaju zdarzenia.  
  
 Mimo `Handles` że klauzula jest standardowy sposób kojarzenia zdarzenia z programem obsługi zdarzeń, jest ograniczona do kojarzenia zdarzeń z programami obsługi zdarzeń w czasie kompilacji.  
  
 W niektórych przypadkach, takich jak zdarzenia skojarzone z formularzy lub formantów, Visual Basic automatycznie wycinki pusty program obsługi zdarzeń i kojarzy go ze zdarzeniem. Na przykład po dwukrotnym kliknięciu przycisku polecenia w formularzu w trybie `WithEvents` projektowania program Visual Basic tworzy pusty program obsługi zdarzeń i zmienną dla przycisku polecenia, jak w poniższym kodzie:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler i RemoveHandler  
 Instrukcja `AddHandler` jest podobna do klauzuli, `Handles` w tym zarówno pozwalają określić program obsługi zdarzeń. Jednak `AddHandler`, używane `RemoveHandler`z , zapewnia `Handles` większą elastyczność niż klauzula, co pozwala dynamicznie dodawać, usuwać i zmieniać program obsługi zdarzeń skojarzony ze zdarzeniem. Jeśli chcesz obsługiwać udostępnione zdarzenia lub zdarzenia ze `AddHandler`struktury, musisz użyć programu .  
  
 `AddHandler`przyjmuje dwa argumenty: nazwę zdarzenia od nadawcy zdarzenia, takich jak formant, i wyrażenie, które ocenia delegata. Nie trzeba jawnie określić klasę delegata podczas korzystania `AddHandler`, ponieważ instrukcja `AddressOf` zawsze zwraca odwołanie do pełnomocnika. Poniższy przykład kojarzy program obsługi zdarzeń ze zdarzeniem wywoływanym przez obiekt:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, który odłącza zdarzenie od programu obsługi zdarzeń, `AddHandler`używa tej samej składni co . Przykład:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 W poniższym przykładzie program obsługi zdarzeń jest skojarzony ze zdarzeniem, a zdarzenie jest wywoływane. Program obsługi zdarzeń przechwytuje zdarzenie i wyświetla komunikat.  
  
 Następnie pierwszy program obsługi zdarzeń jest usuwany i inny program obsługi zdarzeń jest skojarzony ze zdarzeniem. Gdy zdarzenie jest wywoływane ponownie, wyświetlany jest inny komunikat.  
  
 Na koniec drugi program obsługi zdarzeń jest usuwany i zdarzenie jest wywoływane po raz trzeci. Ponieważ nie ma już programu obsługi zdarzeń skojarzonego ze zdarzeniem, nie jest podejmowana żadna akcja.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Obsługa zdarzeń dziedziczonych z klasy podstawowej  
 *Klasy pochodne*— klasy, które dziedziczą cechy klasy podstawowej — `Handles MyBase` mogą obsługiwać zdarzenia wywoływane przez ich klasę podstawową przy użyciu instrukcji.  
  
### <a name="to-handle-events-from-a-base-class"></a>Do obsługi zdarzeń z klasy podstawowej  
  
- Zadeklaruj program obsługi zdarzeń `Handles MyBase.`w klasie pochodnej, dodając instrukcję *eventname* do wiersza deklaracji procedury obsługi zdarzeń, gdzie *nazwa zdarzenia* jest nazwą zdarzenia w klasie podstawowej, którą obsługujesz. Przykład:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wskazówki: deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Zawiera opis krok po kroku, jak zadeklarować i podnieść zdarzenia dla klasy.|  
|[Przewodnik: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Pokazuje, jak napisać procedurę obsługi zdarzeń.|  
|[Instrukcje: deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Pokazuje, jak zdefiniować zdarzenie niestandardowe, które umożliwia jego programy obsługi zdarzeń, które mają być wywoływane asynchronicznie.|  
|[Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Pokazuje, jak zdefiniować zdarzenie niestandardowe, które używa pamięci tylko wtedy, gdy zdarzenie jest obsługiwane.|  
|[Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Wyświetla listę typowych problemów, które pojawiają się z obsługi zdarzeń w składników dziedziczonych.|  
|[Zdarzenia](../../../../standard/events/index.md)|Omówienie modelu zdarzeń w środowisku .NET Framework.|  
|[Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|W tym artykule opisano sposób pracy ze zdarzeniami skojarzonymi z obiektami Windows Forms.|  
|[Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Zawiera omówienie delegatów w języku Visual Basic.|
