---
title: Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 53f63352503a48ee849580e676b5fe98f3dcf2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492499"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
**Ten temat dotyczy starszych technologia, która została zachowana na potrzeby zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecane w przypadku nowych wdrożeń. Teraz należy opracować aplikacji rozproszonych za pomocą usługi WCF.**  
  
 Istnieją dwa sposoby, aby móc korzystać z usługi WCF z istniejących aplikacji .NET Remoting: integracja i migracji. Integracja umożliwia posiadanie .net Remoting 2.0 i systemem WCF kodem po stronie siebie, umożliwiając ujawniać te same obiekty biznesowych w obu tych technologii jednocześnie bez konieczności modyfikowania Twoje istniejące .net 2.0 usług zdalnych. Integracja wymaga się, że są uruchomione na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 lub nowszej. Jeśli chcesz korzystać z funkcji WCF i nie ma potrzeby przesyłania zgodność z systemów zdalnych 2.0, należy przeprowadzić migrację całej usługi do programu WCF. Migracja z programu .NET Remoting 2.0 do programu WCF wymaga wprowadzenia zmian obiektu zdalnego interfejsu i jego ustawień konfiguracji. Oba te tematy zostały omówione w [z Remoting do programu Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie pojęć](../../../../docs/framework/wcf/conceptual-overview.md)
