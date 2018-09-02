---
title: Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 3f5556eeaf56ac48dd4f1d578ed2e66b90415677
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422948"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
**Ten temat dotyczy technologią starszą, która została zachowana na potrzeby zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecane w przypadku nowych wdrożeń. Teraz należy opracować aplikacje rozproszone przy użyciu usługi WCF.**  
  
 Istnieją dwa sposoby, aby móc korzystać z usługi WCF z istniejącymi aplikacjami wywołaniem funkcji zdalnych .NET: integracji i migracji. Integracja pozwala na korzystanie z platformy .net komunikacji zdalnej w wersji 2.0 i usługi WCF z systemem kodem po stronie siebie, co pozwala na udostępnianie tych samych obiektów firmy za pośrednictwem obie technologie jednocześnie bez konieczności modyfikowania istniejących platformy .net 2.0 komunikacji zdalnej. Integracja wymaga, że działają [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 lub nowszej. Jeśli chcesz korzystać z funkcji WCF i nie ma potrzeby o komunikacji sieciowej zgodność z systemami komunikacji zdalnej w wersji 2.0, należy przeprowadzić migrację całej usługi WCF. Migracja z wywołaniem funkcji zdalnych .NET w wersji 2.0 do programu WCF wymaga wprowadzenia zmian do obiektu zdalnego interfejsu i jego ustawienia konfiguracji. Oba te tematy zostały uwzględnione w [z wywołaniem funkcji zdalnych do programu Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie pojęć](../../../../docs/framework/wcf/conceptual-overview.md)
