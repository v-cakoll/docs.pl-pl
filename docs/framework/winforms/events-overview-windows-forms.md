---
title: Formularze systemu Windows — przegląd zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: 6272da52103e0249112dc4ba717057951d67442f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543720"
---
# <a name="events-overview-windows-forms"></a>Formularze systemu Windows — przegląd zdarzeń
Zdarzenie jest działaniem, które można odpowiedzieć lub "handle" w kodzie. Zdarzenia mogą być generowane przez działanie użytkownika, takie jak kliknięcie myszą lub naciśnięciu klawisza; w kodzie programu lub przez system.  
  
 Aplikacje oparte na zdarzeniach wykonać kod w odpowiedzi na zdarzenie. Każdy formularz i kontroli udostępnia wstępnie zdefiniowany zestaw zdarzeń, które można programować względem. Jeśli wystąpi jedno z tych zdarzeń, a kod w obsłudze skojarzone ze zdarzeniem, ten kod jest wywoływana.  
  
 Typy zdarzeń wywołanych przez obiekt różnią się, ale wiele typów są wspólne dla większości kontrolek. Na przykład będzie obsługiwać większość obiektów <xref:System.Windows.Forms.Control.Click> zdarzeń. Jeśli użytkownik kliknie formularza, możesz pisać kod w postaci <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń jest wykonywane.  
  
> [!NOTE]
>  Wiele zdarzenia występują w połączeniu z innymi zdarzeniami. Na przykład w trakcie właściwości <xref:System.Windows.Forms.Control.DoubleClick> zdarzeń mających miejsce, <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>, i <xref:System.Windows.Forms.Control.Click> wystąpieniu zdarzenia.  
  
 Aby uzyskać informacje o tym, jak podnieść i zużyć zdarzenie, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
## <a name="delegates-and-their-role"></a>Delegaci i ich roli  
 Obiekty delegowane są często używane w ramach klasy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tworzyć mechanizmy obsługi zdarzeń. Delegaty około równoważne do wskaźników funkcji, często używane w [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] i inne języki zorientowane obiektowo. W przeciwieństwie do wskaźników funkcji, obiekty delegowane są zorientowane obiektowo, bezpieczny i bezpieczne. Dodatkowo, gdy wskaźnik funkcji zawiera tylko odwołanie do określonej funkcji, delegata składa się z odwołaniem do obiektu, a odwołuje się do co najmniej jednej metody w obrębie obiektu.  
  
 Ten model zdarzeń wykorzystuje *delegatów* powiązać metod, które są używane do obsługi tych zdarzeń. Delegat umożliwia innych klas zarejestrować dla powiadomień o zdarzeniach, określając metody obsługi. Po wystąpieniu zdarzenia, delegat wywołuje powiązanej metody. Aby uzyskać więcej informacji na temat definiowania obiektów delegowanych, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
 Może być powiązana delegatów, jedną metodę lub wiele metod, określane jako multiemisji. Podczas tworzenia obiektu delegowany dla zdarzenia, użytkownik (lub programu Windows Forms Designer) Utwórz zazwyczaj multiemisji zdarzeń. Rzadkie wyjątków może być zdarzenie, które powoduje określonej procedury (na przykład wyświetlanie okna dialogowego), która nie powtórzysz logicznie wiele razy na zdarzenie. Aby uzyskać informacje o sposobie tworzenia delegata multiemisji, zobacz [jak: Łączenie obiektów delegowanych (obiekty delegowane multiemisji)](~/docs/csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).  
  
 Delegat multiemisji utrzymuje listę wywołania metody, które jest powiązany z. Multiemisji delegować obsługuje <xref:System.Delegate.Combine%2A> metodę, aby dodać metodę do listy wywołań i <xref:System.Delegate.Remove%2A> metodę, aby go usunąć.  
  
 Gdy zdarzenie jest rejestrowane przez aplikację, kontrolka wywołuje zdarzenie, wywołując delegata dla tego zdarzenia. Delegat wywołuje z kolei powiązanej metody. W przypadku typowych (delegować multiemisji) delegata wywołuje każdego powiązanej metodę liście wywołania z kolei zapewniającą powiadomienie jeden do wielu. Ta strategia oznacza, że kontrolki nie trzeba utrzymywać listę obiektów docelowych dla powiadomień o zdarzeniach — delegat obsługuje wszystkie rejestracji i powiadomień.  
  
 Delegatów umożliwia także wiele zdarzeń może być powiązane z tej samej metody, dzięki czemu powiadomienia wiele do jednego. Na przykład zdarzenie kliknięcia przycisku i zdarzenia menu — kliknij polecenie zarówno wywołać ten sam delegata, która następnie wywołuje jednej metody do obsługi tych oddzielnych zdarzeń w taki sam sposób.  
  
 Mechanizm powiązania, używany przy użyciu delegatów jest elementem dynamicznym: Delegat może być powiązana, w czasie wykonywania do dowolnej metody, którego podpis jest zgodny z typem obsługi zdarzeń. Za pomocą tej funkcji można zdefiniować lub zmienić metodę powiązanej zależności od warunku i dynamicznie dołączyć program obsługi zdarzeń do formantu.  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
- [Przegląd procedur obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
