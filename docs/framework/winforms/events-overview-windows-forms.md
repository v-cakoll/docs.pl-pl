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
ms.openlocfilehash: 79d1ba122bd78b33fbc675ea0b0ec681005819cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540104"
---
# <a name="events-overview-windows-forms"></a>Formularze systemu Windows — przegląd zdarzeń
Zdarzenie jest działaniem, które mogą odpowiadać na lub "obsługi" w kodzie. Zdarzenia mogą być generowane przez działanie użytkownika, takie jak kliknięcie myszą lub naciśnięcie klawisza. w kodzie programu; czy przez system.  
  
 Aplikacje oparte na zdarzenie wykonać kod w odpowiedzi na zdarzenie. Każdy formularz i sterowania udostępnia zestaw wstępnie zdefiniowanych zdarzeń, które można zaprogramować przed. Wystąpi jedno z tych zdarzeń, jeśli ma kodu do obsługi zdarzeń skojarzony, ten kod jest wywoływany.  
  
 Typy zdarzeń zgłaszanych przez obiekt różny, ale wiele typów są wspólne dla większości formantów. Na przykład, będzie obsługiwać większość obiektów <xref:System.Windows.Forms.Control.Click> zdarzeń. Jeśli użytkownik kliknie formularza, zostanie wyświetlony kod w postaci <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń jest wykonywany.  
  
> [!NOTE]
>  Wiele zdarzenia występują w połączeniu z innymi zdarzeniami. Na przykład w trakcie z <xref:System.Windows.Forms.Control.DoubleClick> zdarzeń występujących, <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>, i <xref:System.Windows.Forms.Control.Click> wystąpienia zdarzeń.  
  
 Aby uzyskać informacje dotyczące pozyskiwania i zużywać zdarzenia, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
## <a name="delegates-and-their-role"></a>Delegaci i ich roli  
 Obiekty delegowane są często używane w obrębie klasy [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] do tworzenia mechanizmy obsługi zdarzeń. Obiekty delegowane przybliżeniu równe wskaźników funkcji, często używane w [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] i innych języków zorientowane obiektowo. W przeciwieństwie do wskaźników funkcji delegatów są jednak zorientowane obiektowo, bezpieczne i bezpieczna. Ponadto, gdy wskaźnik funkcji zawiera tylko odwołanie do określonej funkcji, delegata składa się z odwołaniem do obiektu i odwołuje się do co najmniej jednej metody w obrębie obiektu.  
  
 Ten model zdarzeń korzysta z *delegatów* powiązać zdarzeń do metod, które są używane do ich obsługi. Delegat umożliwia innych klas zarejestrować powiadomienia o zdarzeniach, określając metoda obsługi. Po wystąpieniu zdarzenia, delegat wywołuje metodę powiązania. Aby uzyskać więcej informacji na temat definiowania delegatów, zobacz [zdarzenia](../../../docs/standard/events/index.md).  
  
 Obiekty delegowane może być powiązana do pojedynczej metody lub wiele metod, określany jako multiemisji. Podczas tworzenia delegata zdarzenia, użytkownik (lub Projektant formularzy systemu Windows) Utwórz zwykle zdarzenie multiemisji. Rzadkie wyjątek może być zdarzenie, które powoduje określonej procedury (na przykład wyświetlanie okna dialogowego), która może nie logicznie powtarzane wielokrotnie na zdarzenie. Aby uzyskać informacje o sposobie tworzenia delegata multiemisji, zobacz [porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](~/docs/csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).  
  
 Delegat multiemisji przechowuje listę wywołania metody, który jest powiązany. Multiemisji delegować obsługuje <xref:System.Delegate.Combine%2A> metody w celu dodania do listy wywołania metody i <xref:System.Delegate.Remove%2A> metodę, aby go usunąć.  
  
 Gdy zdarzenie jest rejestrowane przez aplikację, formantu zgłasza zdarzenie, wywołując delegowanie dla tego zdarzenia. Delegat z kolei wywołuje metodę powiązania. W przypadku najbardziej typowych (Multiemisja delegować) delegat wywołuje każdej powiązanej metody na liście wywołania z kolei zapewniające powiadomienie o jeden do wielu. Ta strategia oznacza, że formantu nie trzeba utrzymywać listę obiektów docelowych powiadomienia o zdarzeniach — delegat obsługuje wszystkie rejestracji i powiadomień.  
  
 Delegatów również włączyć wiele zdarzeń może być powiązane z tej samej metody, dzięki czemu powiadomienia wiele do jednego. Na przykład zdarzeń kliknięcia przycisków i menu — kliknij polecenie może zarówno wywołanie tej samej delegata, która następnie wywołuje metodę jeden do obsługi tych oddzielnych zdarzeń w taki sam sposób.  
  
 Mechanizm wiązanie używane z obiektów delegowanych jest dynamiczny: Delegat może być powiązana do dowolnej metody, której sygnatura jest zgodna z obsługi zdarzeń w czasie wykonywania. Za pomocą tej funkcji można zdefiniować lub zmienić metoda powiązana, w zależności od warunek i dynamicznie dołączyć program obsługi zdarzeń do formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Przegląd procedur obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
