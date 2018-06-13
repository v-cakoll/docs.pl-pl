---
title: Omówienie manipulacji i bezwładności
ms.date: 03/30/2017
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
ms.openlocfilehash: 7aec2756bfc3a7d4ccd394d54f19428d73b44fcb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744398"
---
# <a name="manipulations-and-inertia-overview"></a>Omówienie manipulacji i bezwładności
*Manipulacje* umożliwić użytkownikom przenoszenie, obracanie i zmień rozmiar elementów interfejsu użytkownika przy użyciu *manipulatory*. Manipulatora reprezentuje myszy lub (w scenariuszu z obsługą dotyku) pióro lub linii papilarnych.  
  
 *Bezwładności* emuluje zachowanie rzeczywistych dla elementów interfejsu użytkownika, które znajdują się w ruchu symulując wymusza tarcia dla elementów. Dzięki temu elementy na stopniowo powolne ich przepływ (liniowego i kątowego) przed przełączeniem do zatrzymania. Ten artykuł zawiera wprowadzenie do manipulacji i bezwładności dla programu .NET Framework.  
  
## <a name="manipulations"></a>Manipulacje  
 Manipulowania traktuje zbiór manipulatory jako obiektu złożonego. Aplikacja może śledzić zmian obiektu złożonego zamiast pojedynczych składników.  
  
 Należy wziąć pod uwagę obrazu na poniższej ilustracji. Użytkownik może być manipulatory dwóch przenoszenie, obracanie i skalowanie obrazu. Zmiany w każdym manipulatora interpretowania wraz z innymi manipulatory.  
  
 Na przykład, jeśli masz dwie manipulatory (1 i 2) w obrazie i Przenieś manipulatora 1 w + kierunku Y (wyłączone), zmiany w obrazie zależy od co się dzieje z manipulatora 2. Jeśli manipulatora 2 zostanie przesunięta + kierunku Y (wyłączone), po prostu przeniesieniu + kierunku Y. Ale jeśli manipulatora 2 nie ulega zmianie lub przenosi kierunku -Y (w górę), obrazu jest mniejszy lub obrócony.  
  
 ![Zdjęcie wirtualnych, które są manipulowanie dwoma palcami. ] (../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 Obraz jest modyfikowany w zakresie przez dwa manipulatory  
  
 Manipulowanie przetwarzania zapewniają strukturę, która monitoruje podzbiór manipulatory i interpretuje je tak, jakby działają razem, zamiast niezależnie. Można utworzyć kilka manipulowania obiektów procesora równocześnie, po jednej dla każdego elementu interfejsu użytkownika można manipulować w aplikacji. Procesor manipulowania jest informowany o który urządzenia, aby przyjrzeć się wejściowe i zgłasza manipulacje za pośrednictwem [zdarzenia platformy .NET](http://msdn.microsoft.com/library/17sde2xt.aspx).  
  
 Procesor manipulowanie nie ma informacji na temat konkretnego elementu jest zmieniany. Aplikacja oddzielnie stosuje te zmiany do elementu specyficzne dla aplikacji. Na przykład aplikacja stosuje przekształcenia do obrazu lub ponownie rysuje go, aby wyświetlić ją w nowej lokalizacji lub z nowego rozmiaru i orientacji.  
  
 Manipulacje są przeznaczone dwuwymiarowa (2-d) [affine — przekształcenia](http://msdn.microsoft.com/library/ms533810\(VS.85\).aspx). Przekształcenia te obejmują tłumaczenia, obracanie i skalowanie.  
  
### <a name="parts-of-a-manipulation"></a>Części manipulowania  
 Manipulowania jest kolekcją <xref:System.Windows.Input.Manipulations.Manipulator2D> obiektów. Tym manipulowanie agregacji jest reprezentowana przez punktem początkowym i elipsy. Punktem początkowym jest średnią pozycja wszystkich manipulatory, które są manipulowanie elementu. Elipsy ma radius, będącą średni odległość od źródła do każdego z <xref:System.Windows.Input.Manipulations.Manipulator2D> obiektów.  
  
 ![Części manipulowania. ] (../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 Dwa manipulatory (1 i 2), pochodzenia i elipsy Określ manipulowania  
  
 Manipulatory są dodawane, przenieść lub usunąć dla elementu interfejsu użytkownika, aktualizacje aplikacji <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu przez wywołanie metody <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metody. Po rozpoczęciu najpierw operowanie, <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> zdarzenia.  
  
> [!NOTE]
>  Manipulowanie przetwarzania jest bardziej wydajne, gdy jest używany w środowisku aktualizacji na podstawie ramki. Korzystając z manipulacji przetwarzania w aplikacji Microsoft XNA, to nie ma znaczenia ponieważ XNA framework zapewnia aktualizacji na podstawie ramki za pomocą [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metody. W innym środowisku (na przykład WinForms), czasami trzeba podać własną logikę na podstawie ramki do zbierania manipulacje i okresowo wysyłają je do <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metody jako zadanie wsadowe.  
  
 Jako numer manipulatory lub ich zmiana położenia <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> zdarzenia. Właściwości <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> obiekt, który jest przekazywany do <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> obsługi zdarzeń Określ zmiany w pochodzenia, skalowania, obrotu i translacji od czasu ostatniego zdarzenia. Pochodzenie operowanie zmienia manipulatory przenoszenia i gdy manipulatory są dodawane lub usuwane. Wartości tłumaczenia określają, ile X i Y przenoszenie operowanie obejmuje.  
  
 Przy użyciu nowych wartości, aplikację ponownie rysuje elementu interfejsu użytkownika.  
  
 ![Manipulowanie po kontakcie A przeniesione z prawej strony. ] (../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 Manipulatora 1 przenosi i powoduje, że punkt początkowy zmienić  
  
 Po usunięciu ostatniego manipulatora, który jest skojarzony z operowanie z <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> obiektu <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> zdarzenia.  
  
### <a name="the-manipulation-processing-model"></a>Manipulowanie przetwarzania modelu  
 Procesor manipulowania wykorzystuje model bezpośredniego użycia. W tym modelu prostego aplikacji musi przejść pomyślnie wszystkie szczegóły zdarzenia wejściowe do manipulowania procesora. Zdarzenie wejściowy może zostać wywołane przez żadnych danych pierwotnych, takie jak urządzenie myszy, Pióro lub linii papilarnych. Ten proces zapewnia mechanizm filtrowania bezpośredniego i modelu prosty sposób użycia, więc wsadowego aplikacji wejściowego zdarzeń, gdy jest to niezbędne.  
  
 Dla aplikacji do dołączenia wejściowego podstawowego procesu manipulowania tworzy <xref:System.Windows.Input.Manipulations.Manipulator2D> strukturę na podstawie danych wejściowych pierwotny i przekazuje struktury przy użyciu procesora manipulowania <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> — metoda. Procesor manipulacji następnie wywołuje zdarzenia, które aplikacja musi obsługiwać aktualizacji programu visual component w odpowiedni sposób.  
  
 ![Przepływ bezpośrednio manipulacje&#45;model zastosowania. ] (../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 Manipulowanie przetwarzania modelu  
  
## <a name="inertia"></a>Bezwładności  
 Działania procesora bezwładności umożliwia aplikacjom ekstrapolacja symulując zachowanie rzeczywistych lokalizacji, orientację i inne właściwości elementu interfejsu użytkownika.  
  
 Na przykład gdy użytkownik szybkich ruchów element, jego można kontynuować przenoszenie, zwalnia, a następnie powoli zatrzymać. Działania procesora bezwładności implementuje to zachowanie, powodując podobne wartości 2-D (pochodzenia, skalowania, tłumaczenia i obrotu) zmiany w określonym czasie szybkością określone.  
  
 Jako przetwarzania manipulowania procesora bezwładności nie ma informacji o jeden z elementów interfejsu użytkownika. W odpowiedzi na zdarzenia, które są generowane na <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> obiekt aplikacji oddzielnie stosuje te zmiany do elementu specyficzne dla aplikacji.  
  
 Przetwarzanie manipulacji i bezwładności przetwarzania są często używane razem. Swoje interfejsy są podobne i zdarzenia, które pobierają one są (w niektórych przypadkach) identyczne. Ogólnie rzecz biorąc przetwarzania bezwładności rozpoczyna się po zakończeniu operowanie elementu interfejsu użytkownika. Jest to osiągane przez nasłuchiwanie <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> zdarzeń i uruchamianie bezwładności przetwarzania z tej obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.Manipulations>
