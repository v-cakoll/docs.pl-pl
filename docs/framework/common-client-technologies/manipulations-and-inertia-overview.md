---
title: Omówienie manipulacji i bezwładności
ms.date: 03/30/2017
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
ms.openlocfilehash: 93d995d7afec24dedf168274fe29f6a250c0a532
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845817"
---
# <a name="manipulations-and-inertia-overview"></a>Omówienie manipulacji i bezwładności
*Manipulacje* umożliwić użytkownikom przenoszenie, obracać i zmień rozmiar elementów interfejsu użytkownika przy użyciu *manipulatory*. Manipulator reprezentuje myszy lub (w przypadku komputerów z obsługą dotyku) pióro lub linii papilarnych.  
  
 *Bezwładności* emuluje zachowanie rzeczywistych dla elementów interfejsu użytkownika, które znajdują się w ruchu przez symulowanie wymusza zajmowania się do elementów. Dzięki temu elementy, aby stopniowo wolno ich przepływ (liniowych i angular) przed przełączeniem do zatrzymania. Ten artykuł zawiera wprowadzenie do manipulacji i bezwładności w programie .NET Framework.  
  
## <a name="manipulations"></a>Manipulacje  
 Manipulowanie traktuje zbiór manipulatory jako obiektu złożonego. Aplikacja może śledzić zmian obiektu złożonego zamiast pojedynczych składników.  
  
 Należy wziąć pod uwagę obrazu na poniższej ilustracji. Użytkownika można użyć dwóch manipulatory przenieść, obracać i skalować obrazu. Zmiany w każdej manipulator są interpretowane wraz z innymi manipulatory.  
  
 Na przykład, jeśli masz dwa manipulatory (1 i 2) w obrazie i przenieść manipulator 1 w + kierunku Y (w dół), zmiany w obrazie zależy od co stanie się manipulator 2. Jeśli manipulator 2 również przesuwa się + kierunku Y (w dół), obraz, który po prostu przenosi + kierunku Y. Ale jeśli nie zmienia się manipulator 2 lub przesunie się w kierunku -Y (up), obrazu jest mniejszy lub obrócony.  
  
 ![Zdjęcie wirtualnego są manipulowanie dwóch palców. ](../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 Obraz jest przetwarzany przez dwa manipulatory  
  
 Manipulowanie przetwarzania udostępnia strukturę, która monitoruje podzbiór manipulatory i interpretuje je tak, jakby działają razem, zamiast niezależnie. Można utworzyć kilka manipulowania obiektów procesora równocześnie, jeden dla każdego elementu interfejsu użytkownika być przetwarzane w aplikacji. Procesor manipulowania jest informowany o którym urządzenia do obserwowania wejściowe i wysyła raporty manipulacje za pośrednictwem [zdarzenia .NET](../../../docs/standard/events/index.md).  
  
 Procesor manipulacji nie zawiera informacji na temat konkretnego elementu, który jest on przetwarzany. Aplikacja oddzielnie stosuje te zmiany do elementu specyficzne dla aplikacji. Na przykład aplikacja stosuje przekształcenia do obrazu lub odrysowuje go, aby wyświetlić je w nowej lokalizacji lub za pomocą nowego rozmiaru i orientacji.  
  
 Manipulacje są przeznaczone dla dwuwymiarowa (2-D) [affine — przekształcenia](/windows/desktop/gdiplus/-gdiplus-transformations-use). Przekształcenia te obejmują tłumaczenie, obracać i skalować.  
  
### <a name="parts-of-a-manipulation"></a>Części manipulowania  
 Manipulowanie to zbiór <xref:System.Windows.Input.Manipulations.Manipulator2D> obiektów. Tym manipulowanie agregacji jest reprezentowany przez punktem początkowym i elipsy. Punktem początkowym jest średnia pozycja manipulatory wszystkie, które są manipulowanie elementu. Elipsy ma usługi radius, będącego średni odległości ze źródła do poszczególnych <xref:System.Windows.Input.Manipulations.Manipulator2D> obiektów.  
  
 ![Części manipulowania. ](../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 Manipulatory dwóch (1 i 2), pochodzeniu i elipsy Określ manipulowania  
  
 Gdy manipulatory są dodawane, przeniesione lub usunięte, aby element interfejsu użytkownika, aplikacja aktualizuje <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu przez wywołanie metody <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metody. Podczas modyfikowania rozpoczyna się najpierw, <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> zdarzenie jest wywoływane.  
  
> [!NOTE]
>  Manipulowanie przetwarzania jest bardziej wydajne, gdy jest używana w środowiskach opartych na klatkach aktualizacji. Korzystając z przetwarzania w aplikacji Microsoft XNA manipulowania, to nie ma znaczenia, ponieważ program XNA framework zawiera opartych na klatkach aktualizacji za pomocą [Game.Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metody. W innym środowisku (na przykład WinForms), może być konieczne zapewnienie własnej logiki opartych na klatkach zbieranie manipulacje i okresowo wysyłają je do <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metody jako zadania wsadowego.  
  
 Jako liczba manipulatory lub ich zmiana położenia <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> zdarzenie jest wywoływane. Właściwości <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> obiekt, który jest przekazywany do <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> program obsługi zdarzeń Określanie zmian w pochodzenia, skala, obrotu i tłumaczenia, które miały miejsce od ostatniego zdarzenia. Pochodzenie operowanie zmienia manipulatory przenoszenia i gdy manipulatory są dodawane lub usuwane. Tłumaczenie wartości wskazują, ile operowanie obejmuje przenoszenie X lub Y.  
  
 Przy użyciu nowych wartości, aplikacja odrysowuje elementu interfejsu użytkownika.  
  
 ![Manipulowanie nawiązaniu kontaktu A przeniesione z prawej strony. ](../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 Manipulator 1 przenosi i powoduje, że punkt początkowy zmienić  
  
 Po usunięciu ostatniego manipulator, który jest skojarzony z operowanie z <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> zdarzenie jest wywoływane.  
  
### <a name="the-manipulation-processing-model"></a>Manipulowanie przetwarzania modelu  
 Procesor manipulowania korzysta z modelu użycia bezpośrednich. Za pomocą tego prostego modelu aplikacji musi przejść pomyślnie wszystkie szczegóły zdarzenia wejściowe do manipulowania procesora. Dane wejściowe zdarzenia mogą być zgłaszany przez żadnych danych pierwotnych, takie jak urządzenie myszy, Pióro lub linii papilarnych. Ten proces zapewnia mechanizm filtrowania bezpośrednie i prosty sposób użycia modelu, więc wsadowego aplikacji wprowadź zdarzenia, gdy jest to konieczne.  
  
 Dla aplikacji, aby uwzględnić wejściowego podstawowego w procesie manipulowania, tworzy <xref:System.Windows.Input.Manipulations.Manipulator2D> struktura dane wejściowe pierwotny i przekazuje struktury za pomocą procesora manipulowania <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metody. Manipulowanie procesora, a następnie wywołuje zdarzenia, które aplikacja musi obsłużyć do zaktualizowania wizualnego składnika w odpowiedni sposób.  
  
 ![Przepływ bezpośrednie manipulacje&#45;modelem użycia. ](../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 Manipulowanie przetwarzania modelu  
  
## <a name="inertia"></a>Bezwładności  
 Procesor bezwładności umożliwia aplikacjom ekstrapolację lokalizacji, orientacji i inne właściwości elementu interfejsu użytkownika, symulując zachowanie rzeczywistych.  
  
 Na przykład po użytkownik szybkich ruchów elementu, go można dalej poruszać, zwalnianie i powoli zatrzymać. Procesor bezwładności implementuje to zachowanie, powodując przekształceniem afinicznym wartości 2-D (pochodzenia, skala, tłumaczenia i obrót) zmiany w określonym czasie stawki określone.  
  
 Jako z przetwarzaniem manipulowania bezwładności procesor nie zawiera informacji o jeden z elementów interfejsu użytkownika. W odpowiedzi na zdarzenia, które są wywoływane na <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> obiektu aplikacji oddzielnie stosuje te zmiany do elementu specyficzne dla aplikacji.  
  
 Przetwarzanie manipulacji i bezwładności przetwarzania są często używane razem. Ich interfejsy są podobne i zdarzenia, które pobierają one (w niektórych przypadkach) identyczne. Ogólnie rzecz biorąc bezwładności przetwarzanie rozpoczyna się po zakończeniu modyfikowania elementu interfejsu użytkownika. Jest to realizowane przez nasłuchiwanie w <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> zdarzeń i uruchomienie bezwładności, przetwarzając je z tego programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.Manipulations>
