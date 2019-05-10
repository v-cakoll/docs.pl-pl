---
title: Zdarzenia (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 5986923b10700b1795886c24343a4b45e6bff46e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616701"
---
# <a name="events-visual-basic"></a>Zdarzenia (Visual Basic)
Projekt programu Visual Studio mogą wizualizować jako szereg procedur, które są wykonywane w kolejności, w rzeczywistości większość programów są oparte na zdarzeniach — czyli przepływem wykonania jest określana przez zewnętrzne wystąpienia o nazwie *zdarzenia*.  
  
 Zdarzenie jest sygnał, który informuje aplikację, która jest przeprowadzana w coś, co jest ważne. Na przykład, gdy użytkownik kliknie kontrolkę w formularzu, formularz może zgłosić `Click` zdarzenia i wywołania procedury, która obsługuje zdarzenie. Zdarzenia umożliwiają również oddzielne zadania do komunikowania się. Powiedz, na przykład, że aplikacja wykonuje zadanie sortowania oddzielnie od głównej aplikacji. Jeśli użytkownik anuluje sortowania, aplikację można wysłać zdarzenia anulowania, jeśli proces sortowania, aby zatrzymać.  
  
## <a name="event-terms-and-concepts"></a>Zdarzenie terminy i pojęcia  
 W tej sekcji opisano definicje terminów i pojęć ze zdarzeniami w języku Visual Basic.  
  
### <a name="declaring-events"></a>Deklarowanie zdarzeń  
 Możesz zadeklarować zdarzenia w obrębie klasy, struktury, moduły i interfejsy, za pomocą `Event` — słowo kluczowe, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Wywoływanie zdarzeń  
 Zdarzenie jest jak wiadomość informującą, że wystąpiło coś, co jest ważne. Czynność emituje komunikat jest nazywany *wywoływanie* zdarzenia. W języku Visual Basic wywoływanie zdarzeń za pomocą `RaiseEvent` instrukcji, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Zdarzenia musi zostać podniesiony w zakresie klasy, modułu lub struktury, gdzie są one zgłoszone. Na przykład klasa pochodna nie mogą wywoływać zdarzeń dziedziczone z klasy podstawowej.  
  
### <a name="event-senders"></a>Nadawców zdarzeń  
 Każdy obiekt może podnoszenie zdarzenia jest *nadawcy zdarzeń*, znane również jako *źródła zdarzeń*. Formularze, formanty i obiekty zdefiniowane przez użytkownika są przykłady nadawców zdarzeń.  
  
### <a name="event-handlers"></a>Programy obsługi zdarzeń  
 *Programy obsługi zdarzeń* są procedury, które są wywoływane, gdy wystąpi zdarzenie odpowiednie. Wszystkie prawidłowe podprocedury mającej pasujący podpis służy jako program obsługi zdarzeń. Nie możesz użyć funkcji jako program obsługi zdarzeń, ponieważ nie zwraca wartości do źródła zdarzenia.  
  
 Visual Basic używa standardowej konwencji nazewnictwa dla procedury obsługi zdarzeń, które łączy nazwa nadawcy zdarzeń, podkreślenia i nazwa zdarzenia. Na przykład `Click` zdarzeń przycisk o nazwie `button1` będą miały postać `Sub button1_Click`.  
  
> [!NOTE]
>  Firma Microsoft zaleca, że używasz tę konwencję nazewnictwa podczas definiowania obsługi zdarzeń dla własnych zdarzeń, ale nie jest wymagana. można użyć dowolnej nazwy prawidłowe procedurę.  
  
## <a name="associating-events-with-event-handlers"></a>Kojarzenie zdarzeń z programami obsługi zdarzeń  
 Zanim nadaje się program obsługi zdarzeń, należy najpierw powiązać jej ze zdarzeniem przy użyciu `Handles` lub `AddHandler` instrukcji.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents i Klauzula Handles  
 `WithEvents` Instrukcji i `Handles` klauzuli zapewniają deklaratywną metodę określania procedury obsługi zdarzeń. Zdarzenie zgłaszane przez obiekt zadeklarowane za pomocą `WithEvents` — słowo kluczowe może być obsługiwany przez wszystkie procedury z `Handles` instrukcji dla tego zdarzenia, jak pokazano w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 `WithEvents` Instrukcji i `Handles` klauzuli są często najlepszym wyborem dla procedury obsługi zdarzeń, ponieważ używają składni deklaratywnej ułatwia obsługę zdarzeń dla kodu, odczytywania i debugowania. Należy jednak pamiętać o następujących ograniczeniach stosowania `WithEvents` zmiennych:  
  
- Nie można użyć `WithEvents` zmiennej jako zmienną obiektu. Oznacza to, że nie można zadeklarować jako `Object`— należy określić nazwę klasy, kiedy Deklarujesz zmienną.  
  
- Ponieważ zdarzenia udostępnionego nie są związane z wystąpień klasy, nie można użyć `WithEvents` deklaratywne obsługi zdarzeń udostępnionych. Podobnie nie można użyć `WithEvents` lub `Handles` do obsługi zdarzeń z `Structure`. W obu przypadkach można użyć `AddHandler` instrukcję, aby obsługiwać te wydarzenia.  
  
- Nie można utworzyć tablic `WithEvents` zmiennych.  
  
 `WithEvents` Zmienne umożliwiają jedną procedurą obsługi zdarzeń do obsługi co najmniej jeden rodzaj zdarzeń lub jeden lub więcej programów obsługi zdarzeń do obsługi tego samego typu zdarzenia.  
  
 Mimo że `Handles` klauzula jest standardowy sposób kojarzenia zdarzenia z programu obsługi zdarzeń, jest ograniczona do kojarzenia zdarzeń z programami obsługi zdarzeń w czasie kompilacji.  
  
 W niektórych przypadkach takich jak za pomocą zdarzenia związane z formularze lub kontrolki, Visual Basic automatycznie zastępczych się program obsługi zdarzeń pusty i kojarzy ją z zdarzenie. Na przykład po dwukrotnym kliknięciu przycisku w formularzu w trybie projektowania Visual Basic tworzy program obsługi zdarzeń pusty i `WithEvents` zmiennej dla przycisku polecenia tak jak w poniższym kodzie:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler i RemoveHandler  
 `AddHandler` Instrukcji jest podobna do `Handles` w klauzuli, że oba pozwalają na określenie procedury obsługi zdarzeń. Jednak `AddHandler`, który jest używany z `RemoveHandler`, zapewnia większą elastyczność niż `Handles` klauzuli, dzięki czemu możesz dynamicznie dodać, usunąć, a zmiany obsługi zdarzenia powiązanego ze zdarzeniem. Jeśli chcesz obsługiwać lub udostępnione zdarzenia ze struktury, należy użyć `AddHandler`.  
  
 `AddHandler` przyjmuje dwa argumenty: Nazwa zdarzenia z nadawcą zdarzenia, takie jak formant i na wyrażenie obliczane do delegata. Nie trzeba jawnie określić klasa obiektu delegowanego, korzystając z `AddHandler`, ponieważ `AddressOf` instrukcja zawsze zwraca odwołanie do obiektu delegowanego. Poniższy przykład kojarzy program obsługi zdarzeń do zdarzenia wygenerowane przez obiekt:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, rozłącza którego zdarzenie, aby program obsługi zdarzeń korzysta z tej samej składni jako `AddHandler`. Na przykład:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 W poniższym przykładzie program obsługi zdarzeń jest skojarzony ze zdarzeniem, a zdarzenie jest wywoływane. Program obsługi zdarzeń przechwytuje zdarzenia i zostanie wyświetlony komunikat.  
  
 Następnie pierwszego programu obsługi zdarzeń jest usuwany, a program obsługi zdarzeń jest skojarzony ze zdarzeniem. Gdy zdarzenie zostanie zgłoszony ponownie, inny komunikat jest wyświetlany.  
  
 Na koniec drugiego obsługi zdarzeń jest usuwany, a zdarzenie jest wywoływane raz trzeci. Ponieważ istnieje już program obsługi zdarzeń skojarzone ze zdarzeniem, nie podjęto żadnej akcji.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Obsługa zdarzeń dziedziczone z klasy podstawowej  
 *Klasy pochodne*— klasy, które dziedziczą właściwości z klasy bazowej — można obsługiwać zdarzenia wywoływane przez ich przy użyciu klasy bazowej `Handles MyBase` instrukcji.  
  
### <a name="to-handle-events-from-a-base-class"></a>Do obsługi zdarzeń z klasy bazowej  
  
- Zadeklaruj program obsługi zdarzeń w klasie pochodnej, dodając `Handles MyBase.` *eventname* instrukcję, aby wiersz deklaracja procedury obsługi zdarzeń, gdzie *eventname* nazywa się zdarzenie w Klasa bazowa, które obsługujesz. Na przykład:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: Deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Instrukcje krok po kroku opisano sposób deklarowania i wywoływanie zdarzeń klasy.|  
|[Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Pokazuje, jak napisać procedury obsługi zdarzeń.|  
|[Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Pokazuje, jak zdefiniować niestandardowe zdarzenie, które umożliwia jej procedury obsługi zdarzeń do wywołania asynchronicznego.|  
|[Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Pokazuje, jak w celu zdefiniowania niestandardowych zdarzeń, która używa pamięci tylko wtedy, gdy zdarzenie jest obsługiwane.|  
|[Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Zawiera listę typowych problemów, które wynikają z programami obsługi zdarzeń w składników odziedziczonych.|  
|[Zdarzenia](../../../../standard/events/index.md)|Zawiera omówienie modelu zdarzeń w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].|  
|[Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|W tym artykule opisano sposób pracy ze zdarzeniami związane z obiektami Windows Forms.|  
|[Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Omówienie delegatów w języku Visual Basic.|
