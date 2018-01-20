---
title: Entity Data Model
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1a1bdeffcc85383d241c277240187ede41401cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="entity-data-model"></a>Entity Data Model
Modelu danych jednostki (EDM) to zestaw kwestie dotyczące struktury danych, niezależnie od jego przechowywanych formularza. EDM obiektowy opisanego przez Chen Peterowi w 1976 modelu Relacja jednostki, ale również oparty na modelu Relacja jednostki i zwiększa jego tradycyjnego wykorzystania.  
  
 EDM rozwiązuje problemy, które wynikają z danych przechowywanych w wielu formularzach o. Rozważmy na przykład firma, która przechowuje dane w relacyjnych baz danych, pliki tekstowe, pliki XML, arkusze kalkulacyjne i raporty. Stawiało to znaczące trudności w modelowania danych, projekt aplikacji i dostępu do danych. Podczas projektowania aplikacji korzystających z danych, żądania jest napisanie kodu wydajne i łatwy w obsłudze bez ograniczania dostępu do danych wydajne, magazynu i skalowalności. Jeśli dane relacyjne struktury, są bardzo wydajny dostęp do danych, magazynu i skalowalności, ale pisanie kodu wydajne i łatwy w obsłudze staje się coraz trudniejsze. Po danych ma strukturę obiektu, są wycofywane kompromisy: pisanie kodu wydajne i łatwy w obsłudze odbywa się kosztem dostępu do danych wydajne, magazynu i skalowalności. Nawet jeśli znajdują się kompromisu między tymi kompromis, wyzwania wystąpić, gdy dane są przenoszone z jednego formularza do innego. Modelu danych jednostki uwzględniają te problemy przez opisujące struktury danych pod względem jednostki i relacje, które są niezależne od żadnego schematu magazynu. Dzięki temu formularzu przechowywanych danych nie ma zastosowania do projektowania aplikacji i opracowywania. I, ponieważ jednostki i relacje opisano struktury danych, ponieważ jest używany w aplikacji (nie jego przechowywanych formularz), można rozwijać w miarę rozwoju środowisko aplikacji.  
  
 A `conceptual model` jest reprezentację określonej struktury danych jako jednostki i relacje i zazwyczaj jest zdefiniowany w języku specyficznego dla domeny (DSL), który implementuje pojęcia EDM. [Schematu koncepcyjnego definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) przykładem języka specyficznego dla domeny. Jednostki i relacje opisane w modelu koncepcyjnym można traktować jako abstrakcje obiektów i skojarzenia w aplikacji. Umożliwia deweloperom skoncentrować się na model koncepcyjny bez obawy schemat magazynu i umożliwia im to wydajności i łatwości konserwacji na uwadze do pisania kodu. W tym samym czasie projektantów schematu magazynu można skoncentrować się na wydajność dostępu do danych, magazynu i skalowalności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Tematy w tej sekcji opisano pojęcia związane z modelu danych jednostki. Wszelkie DSL, który implementuje EDM powinna zawierać pojęcia opisane w tym miejscu. Należy pamiętać, że [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa pliku CSDL, aby zdefiniować modele koncepcyjne. Aby uzyskać więcej informacji, zobacz [specyfikacji pliku CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Model danych jednostki: Przestrzenie nazw](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Model danych jednostki: Typy danych pierwotnych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Model danych jednostki: Dziedziczenie](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [punkt końcowy skojarzenia](../../../../docs/framework/data/adonet/association-end.md)  
  
 [skojarzenie i liczebność](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [zestaw skojarzeń](../../../../docs/framework/data/adonet/association-set.md)  
  
 [punkt końcowy zestawu skojarzeń](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [typ skojarzenia](../../../../docs/framework/data/adonet/association-type.md)  
  
 [typ złożony](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [kontener jednostek](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [typ jednostki](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [aspekt](../../../../docs/framework/data/adonet/facet.md)  
  
 [właściwość klucza obcego](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [funkcja zadeklarowana modelu](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [funkcja zdefiniowana przez model](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [właściwość nawigacji](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [właściwość](../../../../docs/framework/data/adonet/property.md)  
  
 [ograniczenie integralności referencyjnej](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Omówienie plików edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Specyfikacja CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
