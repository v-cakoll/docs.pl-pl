---
title: "Dodatki i rozszerzalność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e4d336992be216178b1237c9f43bffb3de61fba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="add-ins-and-extensibility"></a>Dodatki i rozszerzalność
<a name="top"></a>Dodatki Podaj rozszerzonych funkcji lub usług dla aplikacji hosta. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zapewnia model programowania, w której deweloperzy mogą używać w celu opracowywania dodatków i aktywować je w aplikacji hosta. Model osiąga to, tworząc potok komunikacji między hostem a dodatku. Model jest zaimplementowana przy użyciu typów w <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, i <xref:System.AddIn.Contract> przestrzeni nazw.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Dodatek modelu](#addin_model)  
  
-   [Dodatki i hostów](#distinguishing_between_addins_and_hosts)  
  
-   [Tematy pokrewne](#related_topics)  
  
-   [Dokumentacja](#reference)  
  
> [!NOTE]
>  Dla budynku potoków dodatku, można znaleźć dodatkowe przykładowy kod i wersji zapoznawczych platformy technologię klienta narzędzi w [zarządzanych rozszerzeń i Dodaj w ramach lokacji w witrynie CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Dodatek modelu  
 Model dodatku składa się z szeregu segmentów, które tworzą dodatku potoku (znanej także jako potok komunikacji), która jest odpowiedzialna za całą komunikację między dodatek i hostem. Potok to model symetryczny komunikacji segmentów, które wymiany danych między dodatek i jej hosta. Tworzenie te segmenty między hostem a dodatek zawiera wymagane warstwy abstrakcji, które obsługuje przechowywanie wersji i izolacja dodatku.  
  
 Na poniższej ilustracji przedstawiono potoku.  
  
 ![Dodaj &#45; w modelu procesu. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Potok dodatku  
  
 Zestawy dla te segmenty nie są wymagane w tej samej domenie aplikacji. Można załadować dodatku do jego własnej nowej domeny aplikacji, do istniejącej domeny aplikacji lub nawet w domenie aplikacji hosta. Do tej samej domenie aplikacji, umożliwiający dodatki współużytkowanie zasobów i kontekstów zabezpieczeń można załadować wiele dodatków.  
  
 Obsługuje modelu dodatku i zaleca, opcjonalne granicę między hostem a dodatku, nazywanego granica izolacji (znanej także jako granic zdalnych). Tę granicę można granice domeny lub procesu aplikacji.  
  
 Segment kontraktu w środku potoku jest ładowany do zarówno domeny aplikacji hosta, jak i dodatku domeny aplikacji. Kontrakt definiuje metody wirtualne który hoście i Użyj dodatku do programu exchange typów ze sobą.  
  
 Do przekazywania granica izolacji, typy muszą być umów lub typów możliwych do serializacji. Typy, które nie umów lub typów możliwych do serializacji muszą zostać skonwertowane do kontraktów segmentami karty w potoku.  
  
 Widok segmentów potoku są abstrakcyjnych klas podstawowych lub interfejsów, które dostarczają hosta i Dodaj w widoku metody, które mają, zgodnie z umową.  
  
 Aby uzyskać więcej informacji o tworzeniu segmentów potoku, zobacz [rozwój potoku](../../../docs/framework/add-ins/pipeline-development.md).  
  
 W kolejnych sekcjach opisano funkcje modelu dodatku.  
  
### <a name="independent-versioning"></a>Niezależnie od wersji  
 Model dodatku pozwala niezależnie hostów i dodatki do wersji. W związku z tym modelem dodatku umożliwia następujące scenariusze:  
  
-   Tworzenie kart, które umożliwia hosta dodatku skompilowany dla wcześniejszych wersji programu host.  
  
-   Tworzenie adaptera, które umożliwia hosta dodatku utworzony przy użyciu nowszej wersji hosta.  
  
-   Tworzenie adaptera hosta do użycia dodatków umożliwia skompilowany dla innego hosta.  
  
### <a name="discovery-and-activation"></a>Odnajdywanie i aktywacji  
 Dodatek można aktywować przy użyciu tokenu z kolekcji, reprezentująca dodatki znaleziono z magazynu informacji. Dodatki są znaleziony podczas przeszukiwania dla typu, który definiuje widoku hosta dodatku. Można również znaleźć określonego dodatku według typu, który definiuje dodatku. Magazyn informacji składa się z dwóch plików pamięci podręcznej: Magazyn potoku i Magazyn dodatków.  
  
 Aby uzyskać informacji na temat aktualizowania i ponowne kompilowanie magazynu informacji, zobacz [dodatku odnajdywania](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421). Uzyskać informacji o aktywacji dodatków, zobacz [dodatku aktywacji](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) i [porady: uaktywnić dodatki z różnych izolacji i zabezpieczeń](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Poziom izolacji i procesów zewnętrznych  
 Model dodatku obsługuje kilka poziomów izolacji między dodatek i jej hosta lub dodatków. Te poziomy od najmniej izolowanym, są następujące:  
  
-   Dodatek jest uruchamiany w tej samej domenie aplikacji hosta. Nie jest to zalecane, ponieważ utratę izolacji i zwalniania możliwości, które można uzyskać, korzystając z różnych domen aplikacji.  
  
-   Wiele dodatki są ładowane do tej samej domenie aplikacji, która różni się od domeny aplikacji używana przez hosta.  
  
-   Każdy dodatek jest załadowany wyłącznie do własnej domeny aplikacji. Jest to najbardziej typowe poziom izolacji.  
  
-   Wiele dodatki są ładowane do tej samej domeny aplikacji w procesie zewnętrznym.  
  
-   Każdy dodatek jest załadowany wyłącznie do własnej domeny aplikacji w procesie zewnętrznym. Jest to najbardziej izolowanego scenariusz.  
  
 Aby uzyskać więcej informacji o używaniu procesów zewnętrznych, zobacz [porady: uaktywnić dodatki z różnych izolacji i zabezpieczeń](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Zarządzanie okresem istnienia  
 Ponieważ model dodatku obejmuje granic domeny i procesu aplikacji, wyrzucanie elementów bezużytecznych przez samego siebie nie wystarcza do wydania i odzyskiwanie obiektów. Model dodatku zapewnia mechanizm zarządzania okresu istnienia, który korzysta z tokenów i liczenie odwołań i zwykle nie wymaga dodatkowego programowania. Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Powrót do początku](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Dodatki i hostów  
 Różnica między dodatek i hosta jest jedynie, że host jest taki, który uaktywnia dodatku. Host może być większy dwóch, takie jak aplikacja edytora i jego pisowni; lub hosta może być mniejszy z dwóch, takich jak klientem obsługi wiadomości błyskawicznych osadza odtwarzacza multimedialnego. Model dodatku obsługuje dodatki w scenariuszach klienta i serwera. Przykładami dodatki serwera dodatków, które dostarczają serwerów poczty antywirusowym, filtry i ochrony IP. Klient dodatku przykładami odwołanie dodatków dla edytory tekstów, specjalne funkcje dla programów grafiki i gry i antywirusowe dla klientów lokalnych poczty e-mail.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Opracowywanie potoku](../../../docs/framework/add-ins/pipeline-development.md)|W tym artykule opisano potok komunikacji segmentów z aplikacji hosta do dodatku. Przykłady kodu w wskazówki tematach opisano sposób tworzenia potoku i sposobu wdrażania segmentów potoku w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].|  
|[Domeny aplikacji i zestawy](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|Opisuje relację między domenami aplikacji, które zapewniają granica izolacji zabezpieczeń, niezawodności i przechowywanie wersji i zestawów.|  
  
 [Powrót do początku](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Powrót do początku](#top)