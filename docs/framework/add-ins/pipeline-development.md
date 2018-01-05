---
title: Opracowywanie potoku
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ad577145c26b9c43e8b7fb3b61f27f374ff9298
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="pipeline-development"></a>Opracowywanie potoku
Potok dodatku jest ścieżką segmentów potoku, w których aplikacja hosta i jego dodatku musi komunikować się ze sobą.  
  
 Na poniższej ilustracji przedstawiono potok komunikacji i jego segmentów.  
  
 ![Dodaj &#45; w modelu procesu. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Potok dodatku  
  
 Aplikacja hosta znajduje się na końcu jednego potoku i dodatek jest na końcu. Począwszy od każdego końca i przenoszenie kierunku środka, zarówno aplikacji hosta, jak i dodatku mają abstrakcyjna klasa podstawowa, definiujący widok modelu obiektu, który zarówno mają. Te typy (klasy) tworzą segmentów potoku dodatku widoku oraz widoku hosta segmentu potoku dodatku. Segment potoku dodatku widoku często zawiera więcej niż jednej klasy abstrakcyjnej, ale klasa, która dodatek dziedziczy jest znany jako podstawy dodatku.  
  
 Segment potoku serwerowe w Dodaj kartę i po stronie hosta karty potoku segmentu convert przepływ typów między ich segmentów potoku widoku i segmentów potoku kontraktu. Centralnej segmentów potoku jest kontraktu, która jest pochodną <xref:System.AddIn.Contract.IContract> interfejsu. Ten kontrakt definiuje metody korzystające z hosta aplikacji i jej dodatek zarówno.  
  
 Jeśli ładowania hosta i dodatek do domeny innej aplikacji, należy granica izolacji oddzielający zakresu aplikacji hosta z zakresu od dodatku. Umowa jest tylko zestawu, który jest ładowany w hosta i domeny aplikacji dodatku. Hosta i Dodaj w każdym odwoływać się tylko do ich widoku metody kontraktu. W związku z tym są rozdzielone przez warstwę abstrakcji z umowy.  
  
 Aby opracować segmentów potoku, należy utworzyć struktury katalogów, które je zawiera. Aby uzyskać więcej informacji na temat wymagań rozwoju i wskazówki w zakresie, zobacz [wymagania rozwój potoku](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 Na poniższej ilustracji przedstawiono typy, które tworzą segmentów potoku. Nazwy typów pokazany na rysunku są dowolne, ale wszystkie typy oprócz hosta i host wyświetlania atrybutów wymagają dodatku, może być rozpoznana za pomocą metod, które utworzyć magazyn informacji.  
  
 ![Dodaj &#45; w modelu z wymaganymi atrybutami typów. ] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Potok dodatku z typami  
  
 W poniższej tabeli opisano segmentów potoku dla aktywacji dodatku. Aby uzyskać więcej informacji na temat te segmenty, zobacz [kontrakty, widoków i kart](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Segment potoku|Opis|  
|----------------------|-----------------|  
|Host|Zestaw aplikacji, która tworzy wystąpienie dodatku.|  
|Widoku hosta dodatku|Reprezentuje widok aplikacji hosta typy obiektów i metody używane do komunikacji z dodatku. W widoku hosta to abstrakcyjna klasa podstawowa lub interfejs.|  
|Adaptery po stronie hosta|Zestaw z co najmniej jednej klasy, który dostosowuje metod do i z umowy.<br /><br /> Ten segment potoku jest identyfikowane za pomocą <xref:System.AddIn.Pipeline.HostAdapterAttribute> atrybutu.<br /><br /> Zestawy wielomodułowe nie są obsługiwane.|  
|Kontrakt|Interfejs, który jest pochodną <xref:System.AddIn.Contract.IContract> interfejsu i który definiuje protokół komunikacji typów między hostem a jego dodatku.<br /><br /> Ten segment potoku jest identyfikowany przez ustawienie <xref:System.AddIn.Pipeline.AddInContractAttribute> atrybutu.|  
|Dodawanie strony karty|Zestaw z co najmniej jednej klasy, który dostosowuje metod do i z umowy.<br /><br /> Ten segment potoku jest identyfikowane za pomocą <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu.<br /><br /> Każdy zestaw w katalogu serwerowe w Dodaj karty, który zawiera typ, który ma <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atrybutu jest ładowany do dodatku domeny aplikacji.<br /><br /> Każdy zestaw w katalogu Dodaj w stronie jest ładowany w domenie aplikacji.<br /><br /> Zestawy wielomodułowe nie są obsługiwane.|  
|Dodaj w widoku|Zestaw, który reprezentuje Widok dodatku typy obiektów i metod, które są używane do komunikacji z hostem. Widok dodatku jest abstrakcyjna klasa podstawowa lub interfejsu.<br /><br /> Ten segment potoku jest identyfikowane za pomocą <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu.<br /><br /> Każdy zestaw w katalogu AddInViews, który zawiera typ, który ma <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybutu jest ładowany do dodatku domeny aplikacji.|  
|Dodatek|Typem skonkretyzowanym wykonuje usługi hosta.|  
  
## <a name="pipeline-activation-path"></a>Ścieżka aktywacji potoku  
 Na poniższej ilustracji przedstawiono aktywacji typów, gdy dodatek jest aktywny. Przedstawiono również przekazywanie obiektów do hosta, takich jak wyników obliczeń lub kolekcja obiektów. Jest to najbardziej typowym scenariuszem.  
  
 ![Dodaj &#45; w modelu ze ścieżką aktywacji. ] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Ścieżka aktywacji z dodatku do hosta  
  
 Ścieżka aktywacji potoku odbywa się w następujący sposób:  
  
1.  Aktywuje aplikacji hosta z dodatku <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metody.  
  
2.  Widok dodatku, dodatku, Dodaj w stronie karty i zestawów kontraktu są ładowane do dodatku domeny aplikacji.  
  
3.  Wystąpienia karty Dodaj w stronie jest tworzony przy użyciu widoku Dodaj (przy użyciu klasy oznaczona <xref:System.AddIn.Pipeline.AddInBaseAttribute> atrybut) jako jego konstruktora. Dodaj w stronie karty dziedziczy kontraktu.  
  
4.  Karty Dodaj strony, która jest typu kontraktu, są przekazywane granicy izolacji (opcjonalnie) do konstruktora karty po stronie hosta.  
  
5.  Adapter dodatku, po stronie hosta i zestawów kontraktu widoku hosta są ładowane do domeny aplikacji hosta.  
  
6.  Tworzone jest wystąpienie karty po stronie hosta przy użyciu kontraktu, ponieważ jego konstruktora. Adaptery po stronie hosta dziedziczy widoku hosta dodatku.  
  
7.  Host ma dodatku, którego typem hosta widok dodatek i można kontynuować podczas wywoływania metody.  
  
## <a name="walkthroughs"></a>Wskazówki  
 Istnieją trzy tematy wskazówki dotyczące sposobu tworzenia potoki przy użyciu programu Visual Studio:  
  
-   [Przewodnik: tworzenie aplikacji rozszerzalnej](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Opisuje dodatku Kalkulator, który wykonuje dodawania, odejmowania mnożenia i dzielenia obliczeń dla hosta.  
  
-   [Wskazówki: Włączanie zgodności z poprzednimi wersjami zmiana hosta](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Opisuje dodać Kalkulator w możliwości udoskonalone Obliczanie i sposób zachować zgodność z pierwszego Kalkulator dodatku.  
  
-   [Wskazówki: Przekazywanie kolekcje między hostami oraz dodatki](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Opisuje sposób przekazywania zbierania danych za pośrednictwem potoku książki scenariusz magazynu.  
  
## <a name="see-also"></a>Zobacz też  
 [Scenariusze potoku dodatku](http://msdn.microsoft.com/en-us/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [Dodatki i rozszerzalność](../../../docs/framework/add-ins/index.md)
