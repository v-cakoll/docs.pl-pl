---
title: Dodatki i rozszerzalność
ms.date: 03/30/2017
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2485f2ecf0426360dba80d443500a92b5a7af6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510057"
---
# <a name="add-ins-and-extensibility"></a>Dodatki i rozszerzalność
<a name="top"></a> Dodatki zapewniają rozszerzone funkcje lub usługi dla aplikacji hosta. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zapewnia model programowania, które deweloperzy mogą używać do tworzenia dodatków i ich aktywowania w aplikacji hosta. Model osiąga to, tworząc potok komunikacji między hostem a dodatkiem. Model jest implementowany przy użyciu typów w <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, i <xref:System.AddIn.Contract> przestrzeni nazw.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Model dodatku](#addin_model)  
  
-   [Dodatki i hostów](#distinguishing_between_addins_and_hosts)  
  
-   [Tematy pokrewne](#related_topics)  
  
-   [Dokumentacja](#reference)  
  
> [!NOTE]
>  Do tworzenia potoków dodatku, można znaleźć dodatkowe przykłady kodu i narzędzia klienta z podglądem technologii w [zarządzanych rozszerzeń i Dodaj w ramach lokacji w witrynie CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Model dodatku  
 Model dodatku składa się z szeregu segmentów, które tworzą dodatku potoku (znany także jako potok komunikacji), który jest odpowiedzialny za całej komunikacji między dodatkiem a hostem. Potok jest model symetryczne komunikacji segmenty wymianę danych między dodatek i jej hostem. Tworzenie te segmenty między hostem a dodatkiem zapewnia wymagane warstwy abstrakcji, które obsługuje przechowywanie wersji i izolacji dodatku.  
  
 Poniższa ilustracja przedstawia potoku.  
  
 ![Dodaj&#45;w modelu potoku. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Potok dodatku  
  
 Zestawy dla te segmenty nie są wymagane w tej samej domenie aplikacji. Możesz załadować dodatek do jego własnej nowej domeny aplikacji, do istniejącej domeny aplikacji lub nawet do domeny aplikacji hosta. W tej samej domenie aplikacji, która umożliwia dodatków udostępnić zasoby obliczeniowe i konteksty zabezpieczeń, należy załadować wielu dodatków.  
  
 Obsługuje model dodatku, a zaleceniem, opcjonalnie granic między hostem a dodatek, który nazywa się granic izolacji (znany także jako granic wywołaniem funkcji zdalnych). Tą granicą może być granic domeny lub procesu aplikacji.  
  
 Segment umowy w trakcie wykonywania potoku są ładowane do zarówno w domenie aplikacji hosta, jak i dodatku w domenie aplikacji. Kontrakt definiuje metody wirtualnej, hosta i Użyj dodatku do programu exchange typy ze sobą.  
  
 Aby przekazać za pośrednictwem granic izolacji, typy muszą być kontraktów lub typów możliwych do serializacji. Typy, które są nie kontraktów lub typów możliwych do serializacji, muszą zostać skonwertowane do umów segmentami karty w potoku.  
  
 Widok segmenty potoku są abstrakcyjne klasy bazowe lub interfejsów, które umożliwiają hosta i dodatek przy użyciu widoku metody, które współużytkują one zgodnie z definicją w umowie.  
  
 Aby uzyskać więcej informacji o tworzeniu potoku segmentów, zobacz [opracowywanie potoku](../../../docs/framework/add-ins/pipeline-development.md).  
  
 W kolejnych sekcjach opisano funkcje modelu dodatków.  
  
### <a name="independent-versioning"></a>Niezależnie od wersji  
 Model dodatku pozwala niezależnie hostów i dodatki do wersji. W rezultacie modelu dodatków umożliwia następujące scenariusze:  
  
-   Tworzenie adaptera, który umożliwia hosta do użycia dodatku stworzona z myślą o poprzednią wersję hosta.  
  
-   Tworzenie adaptera, który umożliwia hosta do użycia dodatku stworzona z myślą o późniejszą wersję hosta.  
  
-   Tworzenie karty, która umożliwia hosta na używanie dodatków stworzona z myślą o innego hosta.  
  
### <a name="discovery-and-activation"></a>Odnajdywanie i aktywacja  
 Dodatek można aktywować przy użyciu tokenu z kolekcji, reprezentująca dodatki znalezione na podstawie magazynu informacji. Dodatki można znaleźć, wyszukując typ, który definiuje widok hosta dodatków. Można również znaleźć określonego dodatku, typ, który definiuje dodatku. Magazyn informacji składa się z dwóch plików w pamięci podręcznej: store potoku i sklepie dodatku.  
  
 Aby uzyskać informacji na temat aktualizowania i ponownie skompilować Magazyn informacji, zobacz [dodatku odnajdywania](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421). Aby dowiedzieć się, jak uaktywnianie dodatków, zobacz [dodatku aktywacji](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) i [jak: Aktywacja dodatków z różnymi ustawieniami izolacji i zabezpieczeń](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Poziomy izolacji i procesy zewnętrzne  
 Model dodatku obsługuje kilka poziomy izolacji między dodatek i jej hostem lub między dodatków. Począwszy od najmniej izolowane, te poziomy są następujące:  
  
-   Dodatek jest uruchamiany w tej samej domenie aplikacji hosta. Nie jest to zalecane, ponieważ utracisz izolacji i zwalnianie możliwości, które można uzyskać, korzystając z różnych domenach aplikacji.  
  
-   Wielu dodatków są ładowane do tej samej domenie aplikacji, która jest inna niż domena aplikacji używana przez hosta.  
  
-   Każdy dodatek jest ładowany wyłącznie do własnej domeny aplikacji. Jest to najbardziej typowe poziom izolacji.  
  
-   Wielu dodatków są ładowane do tej samej domenie aplikacji w procesie zewnętrznym.  
  
-   Każdy dodatek jest ładowany wyłącznie do własnej domeny aplikacji w procesie zewnętrznym. Jest to najbardziej izolowane scenariusz.  
  
 Aby uzyskać więcej informacji o korzystaniu z zewnętrznego procesów, zobacz [jak: Aktywacja dodatków z różnymi ustawieniami izolacji i zabezpieczeń](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Zarządzanie okresem istnienia  
 Ponieważ model dodatku obejmuje granic domeny i procesu aplikacji, wyrzucanie elementów bezużytecznych samodzielnie nie jest wystarczające, aby zwolnić i odzyskać obiekty. Model dodatku zapewnia mechanizm zarządzania okresem istnienia, który używa tokenów i zliczanie odwołań i zazwyczaj nie wymaga dodatkowego programowania. Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Powrót do początku](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Dodatki i hostów  
 Różnica między dodatek i hosta jest jedynie, że host jest taki, który aktywuje dodatek. Host może być większy z nich, takie jak aplikacja edytora tekstów i jego pisowni; lub host może być mniejszy z nich, takich jak klient wiadomości błyskawicznych, który uwzględnia Windows media player. Model dodatku obsługuje dodatków w scenariuszach klienta i serwera. Przykładami dodatki serwera dodatki, które dostarczają serwerów poczty skanowania antywirusowego, filtry i ochrona. Klient dodatku przykładami dodatki odwołania dla edytorów tekstów specjalne funkcje dla programów grafika i gry i antywirusowe dla klientów poczty e-mail lokalnego.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Opracowywanie potoku](../../../docs/framework/add-ins/pipeline-development.md)|W tym artykule opisano potok komunikacji segmentów aplikacji hosta, aby dodatek. Przykłady kodu w tematach wskazówki, które opisują jak do budowy potoku oraz jak wdrożyć segmentów potoku w programie Visual Studio.|  
|[Domeny aplikacji i zestawy](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|W tym artykule opisano relację między domenami aplikacji, które umożliwiają wyznaczanie granic izolacji zabezpieczeń, niezawodności i przechowywanie wersji i zestawy.|  
  
 [Powrót do początku](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Powrót do początku](#top)