---
title: Zdarzenia (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: b69615a5cf05427a2bfde82af976cfafb41171b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655274"
---
# <a name="events-visual-basic"></a>Zdarzenia (Visual Basic)
Projektu programu Visual Studio może wizualizacji jako szereg procedur, które są wykonywane w kolejności, w rzeczywistości większość programów są zdarzeniami — czyli sposób wykonywania jest określany przez zewnętrznego wystąpienia o nazwie *zdarzenia*.  
  
 Zdarzenie jest sygnał, który informuje o aplikacji, która coś ważne wystąpił. Na przykład, gdy użytkownik kliknie kontrolkę w formularzu, formularz może wiązać się z `Click` zdarzeń i wywołaniu procedury, która obsługuje zdarzenie. Zdarzenia również umożliwić oddzielnych zadań do komunikacji. Powiedz, na przykład, że aplikacja wykonuje zadanie sortowania oddzielnie z głównej aplikacji. Jeśli użytkownik anuluje sortowanie, aplikacja może wysyłać zdarzenie Anuluj poinstruowanie zatrzymanie procesu sortowania.  
  
## <a name="event-terms-and-concepts"></a>Zdarzenie terminy i pojęcia  
 W tej sekcji opisano definicje terminów i pojęć ze zdarzeniami w języku Visual Basic.  
  
### <a name="declaring-events"></a>Deklarowanie zdarzeń  
 Deklarowanie zdarzeń w obrębie klasy, struktury, moduły i przy użyciu interfejsów `Event` — słowo kluczowe, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]  
  
### <a name="raising-events"></a>Wywoływanie zdarzeń  
 Zdarzenie przypomina wiadomość informującą, że coś ważne wystąpił. Emituje komunikat czynnością jest nazywany *wywoływanie* zdarzenia. W języku Visual Basic wywoływanie zdarzeń o `RaiseEvent` instrukcji, jak w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]  
  
 Zdarzenia musi zostać podwyższony w zakresie klasy, modułu lub struktury, gdzie są zadeklarowane. Na przykład klasa pochodna nie mogą wywoływać zdarzeń dziedziczona z klasy podstawowej.  
  
### <a name="event-senders"></a>Nadawców zdarzeń  
 Każdy obiekt może wywołaniem zdarzenia jest *zdarzenia*, znanej także jako *źródło zdarzenia*. Formularze, kontrolki i obiektów zdefiniowanych przez użytkownika przedstawiono nadawców zdarzeń.  
  
### <a name="event-handlers"></a>Programy obsługi zdarzeń  
 *Programy obsługi zdarzeń* są procedur, które są wywoływane, gdy występuje odpowiednie zdarzenie. Wszystkie prawidłowe procedury przy użyciu podpisu zgodnego służy jako program obsługi zdarzeń. Nie możesz użyć funkcji jako program obsługi zdarzeń, ponieważ nie zwraca wartości w źródle zdarzeń.  
  
 Visual Basic używa standardowej konwencji nazewnictwa dla programów obsługi zdarzeń, które łączy nazwę zdarzenia, podkreślenia i nazwa zdarzenia. Na przykład `Click` zdarzeń przycisk o nazwie `button1` będą miały postać `Sub button1_Click`.  
  
> [!NOTE]
>  Firma Microsoft zaleca, aby tę konwencję nazewnictwa służą do definiowania obsługi zdarzeń własne zdarzenia, ale nie jest wymagana. można użyć dowolnej nazwy prawidłowe procedury.  
  
## <a name="associating-events-with-event-handlers"></a>Kojarzenie zdarzenia z obsługi zdarzeń  
 Aby program obsługi zdarzeń stał się można używać, należy najpierw powiązać jej ze zdarzeniem przy użyciu `Handles` lub `AddHandler` instrukcji.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents i Klauzula Handles  
 `WithEvents` Instrukcji i `Handles` klauzuli zapewniają deklaratywne sposób określania obsługi zdarzeń. Zdarzenie zgłaszane przez obiekt zadeklarowana z `WithEvents` — słowo kluczowe są obsługiwane przez wszystkie procedury z `Handles` instrukcji dla tego zdarzenia, jak pokazano w poniższym przykładzie:  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]  
  
 `WithEvents` Instrukcji i `Handles` klauzuli są często najlepszym rozwiązaniem dla programów obsługi zdarzeń, ponieważ używają składni deklaratywnej ułatwia obsługi zdarzeń do kodu, przeczytaj i debugowania. Należy jednak pamiętać następujące ograniczenia stosowania `WithEvents` zmiennych:  
  
-   Nie można użyć `WithEvents` zmiennej jako zmienną obiektu. Oznacza to, że nie można zadeklarować jako `Object`— należy określić nazwę klasy w deklaracji zmiennej.  
  
-   Ponieważ zdarzenia udostępnionego nie są związane z wystąpień klasy, nie można użyć `WithEvents` deklaratywnie obsługi zdarzeń udostępnionego. Podobnie, nie można użyć `WithEvents` lub `Handles` do obsługi zdarzeń z `Structure`. W obu przypadkach można użyć `AddHandler` instrukcji do obsługi tych zdarzeń.  
  
-   Nie można utworzyć tablic `WithEvents` zmiennych.  
  
 `WithEvents` Zmienne umożliwiają jednym programem obsługi zdarzeń do obsługi co najmniej jednego rodzaju zdarzenia lub jeden lub więcej programów obsługi zdarzeń do obsługi tego samego typu zdarzenia.  
  
 Mimo że `Handles` klauzula jest standardowym sposobem Kojarzenie zdarzenia z obsługi zdarzeń, jest ograniczona do kojarzenia zdarzenia z obsługi zdarzeń w czasie kompilacji.  
  
 W niektórych przypadkach takich jak zdarzenia skojarzonego z formularze lub kontrolki, Visual Basic automatycznie zastępcze limit program obsługi zdarzeń pusty i kojarzy ją z zdarzenia. Na przykład po dwukrotnym kliknięciu przycisku polecenia formularza w trybie projektowania, Visual Basic tworzy program obsługi zdarzeń pusty i `WithEvents` zmiennej dla przycisku polecenia, zgodnie z poniższym kodem:  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler i RemoveHandler  
 `AddHandler` Instrukcja jest podobna do `Handles` w klauzuli, że oba umożliwiają określenie programu obsługi zdarzeń. Jednak `AddHandler`używane z `RemoveHandler`, zapewnia większą elastyczność niż `Handles` klauzuli, co umożliwia dynamiczne dodawanie, usuwanie i zmianę programu obsługi zdarzeń skojarzone ze zdarzeniem. Jeśli chcesz obsługiwać lub udostępnionego zdarzenia ze strukturą, należy użyć `AddHandler`.  
  
 `AddHandler` przyjmuje dwa argumenty: Nazwa zdarzenia od nadawcy zdarzenia, takie jak formantu i wyrażenie obliczane do delegata. Nie trzeba jawnie określać klasy obiektu delegowanego przy użyciu `AddHandler`, ponieważ `AddressOf` instrukcji zawsze zwraca odwołanie do obiektu delegowanego. Poniższy przykład skojarzony program obsługi zdarzeń z zdarzenie zgłaszane przez obiekt:  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]  
  
 `RemoveHandler`, które rozłącza zdarzenia z obsługi zdarzeń korzysta z tej samej składni jak `AddHandler`. Na przykład:  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]  
  
 W poniższym przykładzie program obsługi zdarzeń jest skojarzony ze zdarzeniem, a zdarzenie zostanie wywołane. Program obsługi zdarzeń przechwytuje zdarzenia i zostanie wyświetlony komunikat.  
  
 Następnie jest usuwany pierwszego programu obsługi zdarzeń i program obsługi zdarzeń jest skojarzone ze zdarzeniem. Gdy zdarzenie zostanie zgłoszony ponownie, zostanie wyświetlony komunikat inny.  
  
 Na koniec drugiego programu obsługi zdarzeń zostanie usunięty i zdarzenie jest wywoływane raz trzeci. Ponieważ nie jest już skojarzona ze zdarzeniem program obsługi zdarzeń, nie podjęto żadnej akcji.  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Obsługa zdarzeń dziedziczona z klasy podstawowej  
 *Klasy pochodne*— klas, które dziedziczą właściwości od klasy podstawowej — może obsłużyć zdarzenia generowane przez ich przy użyciu klasy podstawowej `Handles``MyBase` instrukcji.  
  
#### <a name="to-handle-events-from-a-base-class"></a>Do obsługi zdarzeń z klasy podstawowej  
  
-   Deklarowanie program obsługi zdarzeń w klasie pochodnej, dodając `Handles MyBase.` *eventname* instrukcji deklaracji w wierszu procedury obsługi zdarzeń, gdzie *eventname* jest nazwą zdarzenia w Klasa podstawowa, które są obsługi. Na przykład:  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: deklarowanie i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Krok po kroku opisano sposób deklarowanie i wywoływanie zdarzeń klasy.|  
|[Przewodnik: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Pokazuje, jak napisać procedury obsługi zdarzeń.|  
|[Instrukcje: deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Pokazuje, jak zdefiniować niestandardowe zdarzenie, które umożliwia jej obsługi zdarzeń ma być wywoływana asynchronicznie.|  
|[Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Pokazuje sposób definiowania niestandardowych zdarzeń, który korzysta z pamięci tylko wtedy, gdy zdarzenie jest obsługiwane.|  
|[Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Wyświetla listę typowych problemów, które wynikają z obsługi zdarzeń w składników odziedziczonych.|  
|[Zdarzenia](../../../../standard/events/index.md)|Zawiera omówienie modelu zdarzeń w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].|  
|[Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Opisuje sposób pracy z zdarzenia związane z obiektami formularzy systemu Windows.|  
|[Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Zawiera omówienie delegatów w języku Visual Basic.|
