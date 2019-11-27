---
title: Zdarzenia
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 666e138a747c480ef9e8b593f8c6233105fcdc93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345118"
---
# <a name="events-visual-basic"></a>Zdarzenia (Visual Basic)
Chociaż można wizualizować projekt programu Visual Studio jako szereg procedur wykonywanych w sekwencji, w rzeczywistości większość programów jest sterowana zdarzeniami — oznacza to, że przepływ wykonywania jest określany przez wystąpienia zewnętrzne nazywane *zdarzeniami*.  
  
 Zdarzenie jest sygnałem, który informuje aplikację o wystąpieniu znaczenia. Na przykład gdy użytkownik kliknie formant w formularzu, formularz może zgłosić zdarzenie `Click` i wywołać procedurę, która obsługuje zdarzenie. Zdarzenia umożliwiają również komunikowanie się z osobnymi zadaniami. Załóżmy na przykład, że aplikacja wykonuje zadanie sortowania niezależnie od głównej aplikacji. Jeśli użytkownik anuluje sortowanie, aplikacja może wysłać zdarzenie anulowania, co powoduje zatrzymanie procesu sortowania.  
  
## <a name="event-terms-and-concepts"></a>Warunki i pojęcia dotyczące zdarzenia  
 Ta sekcja zawiera opis pojęć i koncepcji używanych ze zdarzeniami w Visual Basic.  
  
### <a name="declaring-events"></a>Deklarowanie zdarzeń  
 Zdarzenia deklaruje się w klasach, strukturach, modułach i interfejsach za pomocą słowa kluczowego `Event`, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Wywoływanie zdarzeń  
 Zdarzenie przypomina komunikat informujący o tym, że coś istotny wystąpił. Czynność rozgłaszania wiadomości jest nazywana *podnoszeniem* zdarzenia. W Visual Basic są podniesione zdarzenia za pomocą instrukcji `RaiseEvent`, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Zdarzenia muszą być zgłaszane w zakresie klasy, modułu lub struktury, w której zostały zadeklarowane. Na przykład Klasa pochodna nie może zgłosić zdarzeń dziedziczonych z klasy bazowej.  
  
### <a name="event-senders"></a>Nadawcy zdarzeń  
 Każdy obiekt, który może podnieść zdarzenie, jest *nadawcą zdarzenia*, znanym również jako *Źródło zdarzenia*. Formularze, formanty i obiekty zdefiniowane przez użytkownika są przykładami nadawców zdarzeń.  
  
### <a name="event-handlers"></a>Programy obsługi zdarzeń  
 Procedury *obsługi zdarzeń* są wywoływane, gdy wystąpi odpowiednie zdarzenie. Do obsługi zdarzeń można użyć dowolnej prawidłowej procedury z podpisem zgodnym. Nie można użyć funkcji jako programu obsługi zdarzeń, ponieważ nie może ona zwrócić wartości do źródła zdarzenia.  
  
 Visual Basic używa standardowej konwencji nazewnictwa dla programów obsługi zdarzeń, która łączy nazwę nadawcy zdarzenia, znak podkreślenia i nazwę zdarzenia. Na przykład zdarzenie `Click` przycisku o nazwie `button1` byłoby nazwane `Sub button1_Click`.  
  
> [!NOTE]
> Zalecamy używanie tej konwencji nazewnictwa podczas definiowania obsługi zdarzeń dla własnych zdarzeń, ale nie jest to wymagane. można użyć dowolnej prawidłowej nazwy procedury podrzędnej.  
  
## <a name="associating-events-with-event-handlers"></a>Kojarzenie zdarzeń z obsługą zdarzeń  
 Przed rozpoczęciem korzystania z programu obsługi zdarzeń należy najpierw skojarzyć go ze zdarzeniem przy użyciu instrukcji `Handles` lub `AddHandler`.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents i klauzula Handles  
 Instrukcja `WithEvents` i klauzula `Handles` zapewniają deklaratywny sposób określania programów obsługi zdarzeń. Zdarzenie wywoływane przez obiekt zadeklarowany za pomocą słowa kluczowego `WithEvents` może być obsługiwane przez dowolną procedurę z instrukcją `Handles` dla tego zdarzenia, jak pokazano w następującym przykładzie:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 Instrukcje `WithEvents` i klauzula `Handles` są często najlepszym wyborem dla programów obsługi zdarzeń, ponieważ używana składnia deklaracyjne sprawia, że obsługa zdarzeń ułatwia kod, Odczyt i debugowanie. Należy jednak pamiętać o następujących ograniczeniach dotyczących używania zmiennych `WithEvents`:  
  
- Nie można użyć zmiennej `WithEvents` jako zmiennej obiektu. Oznacza to, że nie można zadeklarować go jako `Object`— należy określić nazwę klasy podczas deklarowania zmiennej.  
  
- Ze względu na to, że zdarzenia udostępnione nie są powiązane z wystąpieniami klasy, nie można użyć `WithEvents`, aby deklaratywnie obsłużyć zdarzenia udostępnione. Podobnie nie można używać `WithEvents` ani `Handles` do obsługi zdarzeń z `Structure`. W obu przypadkach można użyć instrukcji `AddHandler`, aby obsłużyć te zdarzenia.  
  
- Nie można tworzyć tablic zmiennych `WithEvents`.  
  
 zmienne `WithEvents` umożliwiają pojedynczemu programowi obsługi zdarzeń obsłużenie jednego lub więcej rodzajów zdarzeń lub jednego lub kilku programów obsługi zdarzeń w celu obsługi tego samego rodzaju zdarzenia.  
  
 Chociaż klauzula `Handles` jest standardowym sposobem kojarzenia zdarzenia z programem obsługi zdarzeń, jest ograniczone do kojarzenia zdarzeń z procedurami obsługi zdarzeń w czasie kompilacji.  
  
 W niektórych przypadkach, takich jak ze zdarzeniami związanymi z formularzami lub kontrolkami, Visual Basic automatycznie tworzy pustą procedurę obsługi zdarzeń i kojarzy ją ze zdarzeniem. Na przykład po dwukrotnym kliknięciu przycisku polecenia w formularzu w trybie projektowania Visual Basic tworzy pustą procedurę obsługi zdarzeń i zmienną `WithEvents` dla przycisku polecenia, jak w poniższym kodzie:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler i RemoveHandler  
 Instrukcja `AddHandler` jest podobna do klauzuli `Handles` w tym, że oba umożliwiają określenie programu obsługi zdarzeń. Jednak `AddHandler`, używane z `RemoveHandler`, zapewnia większą elastyczność niż klauzula `Handles`, umożliwiając dynamiczne dodawanie, usuwanie i zmienianie obsługi zdarzeń skojarzonych ze zdarzeniem. Jeśli chcesz obsługiwać zdarzenia udostępnione lub zdarzenia ze struktury, musisz użyć `AddHandler`.  
  
 `AddHandler` pobiera dwa argumenty: nazwę zdarzenia od nadawcy zdarzenia, takiego jak kontrolka, i wyrażenie, które daje delegatowi. Nie musisz jawnie podawać klasy delegata przy użyciu `AddHandler`, ponieważ instrukcja `AddressOf` zawsze zwraca odwołanie do delegata. Poniższy przykład kojarzy procedurę obsługi zdarzeń z zdarzeniem wywoływanym przez obiekt:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, która rozłącza zdarzenie z programu obsługi zdarzeń, używa tej samej składni co `AddHandler`. Na przykład:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 W poniższym przykładzie procedura obsługi zdarzeń jest skojarzona ze zdarzeniem, a zdarzenie jest zgłaszane. Procedura obsługi zdarzeń przechwytuje zdarzenie i wyświetla komunikat.  
  
 Następnie Pierwsza procedura obsługi zdarzeń zostanie usunięta i zostanie skojarzona inna procedura obsługi zdarzeń ze zdarzeniem. Gdy zdarzenie zostanie zgłoszone ponownie, zostanie wyświetlony inny komunikat.  
  
 Na koniec Druga procedura obsługi zdarzeń jest usuwana, a zdarzenie jest zgłaszane po raz trzeci. Ze względu na to, że program obsługi zdarzeń nie jest już skojarzony ze zdarzeniem, nie jest podejmowana żadna akcja.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Obsługa zdarzeń dziedziczonych z klasy bazowej  
 *Klasy pochodne*— klasy dziedziczące cechy z klasy podstawowej — mogą obsługiwać zdarzenia zgłoszone przez ich klasę bazową przy użyciu instrukcji `Handles MyBase`.  
  
### <a name="to-handle-events-from-a-base-class"></a>Aby obsłużyć zdarzenia z klasy bazowej  
  
- Zadeklaruj procedurę obsługi zdarzeń w klasie pochodnej przez dodanie instrukcji `Handles MyBase.`*EventName* do wiersza deklaracji procedury obsługi zdarzeń, gdzie *EventName* jest nazwą zdarzenia w obsługiwanej klasie podstawowej. Na przykład:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Stanowisko|Opis|  
|-----------|-----------------|  
|[Przewodnik: deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Zawiera opis krok po kroku dotyczący sposobu deklarowania i zgłaszania zdarzeń dla klasy.|  
|[Przewodnik: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Pokazuje, jak napisać procedurę procedury obsługi zdarzeń.|  
|[Instrukcje: deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Demonstruje sposób definiowania zdarzenia niestandardowego, które umożliwia obsługę zdarzeń asynchronicznie.|  
|[Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Demonstruje sposób definiowania zdarzenia niestandardowego, które używa pamięci tylko wtedy, gdy zdarzenie jest obsługiwane.|  
|[Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Wyświetla listę typowych problemów występujących w przypadku programów obsługi zdarzeń w składnikach dziedziczonych.|  
|[Zdarzenia](../../../../standard/events/index.md)|Omówienie modelu zdarzeń w środowisku .NET Framework.|  
|[Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Opisuje sposób pracy ze zdarzeniami skojarzonymi z obiektami Windows Forms.|  
|[Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Zawiera omówienie delegatów w Visual Basic.|
