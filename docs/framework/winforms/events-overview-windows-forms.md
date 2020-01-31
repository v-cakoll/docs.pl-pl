---
title: Przegląd zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: 59085597789d12ce80648efb77859228e4718a3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743485"
---
# <a name="events-overview-windows-forms"></a>Formularze systemu Windows — przegląd zdarzeń
Zdarzenie jest akcją, na którą można odpowiedzieć lub "dojście" w kodzie. Zdarzenia mogą być generowane przez akcję użytkownika, taką jak kliknięcie myszą lub naciśnięcie klawisza. według kodu programu; lub przez system.

 Aplikacje oparte na zdarzeniach wykonują kod w odpowiedzi na zdarzenie. Każdy formularz i kontrola przedstawia wstępnie zdefiniowany zestaw zdarzeń, dla których można programować. Jeśli wystąpi jedno z tych zdarzeń i kod w skojarzonym programie obsługi zdarzeń, ten kod jest wywoływany.

 Typy zdarzeń wywoływanych przez obiekt różnią się, ale wiele typów jest wspólnych dla większości formantów. Na przykład większość obiektów będzie obsługiwać zdarzenie <xref:System.Windows.Forms.Control.Click>. Jeśli użytkownik kliknie formularz, zostanie wykonany kod w programie obsługi zdarzeń <xref:System.Windows.Forms.Control.Click>.

> [!NOTE]
> Wiele zdarzeń występuje w połączeniu z innymi zdarzeniami. Na przykład w trakcie zdarzenia <xref:System.Windows.Forms.Control.DoubleClick> wystąpią zdarzenia <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>i <xref:System.Windows.Forms.Control.Click>.

 Aby uzyskać informacje na temat sposobu zgłaszania i korzystania ze zdarzenia, zobacz [zdarzenia](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Delegaty i ich rola
 Delegaty są klasami powszechnie używanymi w .NET Framework do kompilowania mechanizmów obsługi zdarzeń. Delegaty są w przybliżeniu równe wskaźnikom funkcji, często używanym w wizualizacjach C++ i innych językach zorientowanych obiektowo. W przeciwieństwie do wskaźników funkcji Delegaty są jednak zorientowane obiektowo, bezpieczne dla typów i bezpieczne. Ponadto, gdy wskaźnik funkcji zawiera tylko odwołanie do konkretnej funkcji, delegat składa się z odwołania do obiektu i odwołuje się do jednej lub więcej metod w obiekcie.

 Ten model zdarzeń używa *delegatów* do wiązania zdarzeń z metodami, które są używane do ich obsługi. Delegat umożliwia innym klasom rejestrację w celu powiadomienia o zdarzeniu przez określenie metody obsługi. Gdy wystąpi zdarzenie, delegat wywołuje metodę powiązaną. Aby uzyskać więcej informacji o definiowaniu delegatów, zobacz [zdarzenia](../../standard/events/index.md).

Delegaty mogą być powiązane z pojedynczą metodą lub z wieloma metodami, nazywanymi multiemisją. Podczas tworzenia delegata dla zdarzenia (lub systemu Windows) zwykle tworzone jest zdarzenie multiemisji. Rzadki wyjątek może być zdarzeniem, które powoduje konkretną procedurę (na przykład wyświetlanie okna dialogowego), które nie powtarzają się wielokrotnie na zdarzenie. Aby uzyskać informacje o sposobach tworzenia delegata multiemisji, zobacz [jak łączyć delegatów (delegatów multiemisji)](../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

 Delegat multiemisji utrzymuje listę wywołań metod, z którą jest powiązana. Delegat multiemisji obsługuje metodę <xref:System.Delegate.Combine%2A>, aby dodać metodę do listy wywołań i metodę <xref:System.Delegate.Remove%2A>, aby ją usunąć.

 Gdy zdarzenie jest rejestrowane przez aplikację, formant wywołuje zdarzenie, wywołując delegata dla tego zdarzenia. Delegat z kolei wywołuje metodę powiązaną. W najbardziej typowym przypadku (delegat multiemisji) delegat wywołuje każdą powiązaną metodę z listy wywołań, która zawiera powiadomienie jeden do wielu. Ta strategia oznacza, że formant nie musi obsługiwać listy obiektów docelowych dla powiadomienia o zdarzeniu — delegat obsługuje wszystkie rejestracje i powiadomienia.

 Delegaty umożliwiają również powiązanie wielu zdarzeń z tą samą metodą, co pozwala na powiadomienie wiele-do-jednego. Na przykład zdarzenie kliknięcia przycisku i menu-polecenie-kliknięcie zdarzenia może wywoływać tego samego delegata, który następnie wywołuje pojedynczą metodę w celu obsługi tych oddzielnych zdarzeń w ten sam sposób.

 Mechanizm powiązań używany z delegatami jest dynamiczny: delegat może być powiązany w czasie wykonywania do dowolnej metody, której sygnatura jest zgodna z programem obsługi zdarzeń. Za pomocą tej funkcji można skonfigurować lub zmienić metodę powiązaną w zależności od warunku i dynamicznie dołączyć procedurę obsługi zdarzeń do kontrolki.

## <a name="see-also"></a>Zobacz także

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Przegląd procedur obsługi zdarzeń](event-handlers-overview-windows-forms.md)
