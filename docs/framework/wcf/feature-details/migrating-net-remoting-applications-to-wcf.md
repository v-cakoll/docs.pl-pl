---
title: Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 863679b5c6333d8049d335f263aa3b1729859d8b
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843312"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
**Ten temat dotyczy technologią starszą, która została zachowana na potrzeby zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecane w przypadku nowych wdrożeń. Teraz należy opracować aplikacje rozproszone przy użyciu usługi WCF.**  
  
 Istnieją dwa sposoby, aby móc korzystać z usługi WCF z istniejącymi aplikacjami wywołaniem funkcji zdalnych .NET: integracji i migracji. Integracja umożliwia wywołaniem funkcji zdalnych .NET w wersji 2.0 i usługi WCF działa obok siebie, co pozwala na udostępnianie tych samych obiektów firmy za pośrednictwem obie technologie jednocześnie bez konieczności modyfikowania istniejącego kodu wywołaniem funkcji zdalnych .NET w wersji 2.0. Integracja wymaga, że działają [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 lub nowszej. Jeśli chcesz korzystać z funkcji WCF i nie ma potrzeby o komunikacji sieciowej zgodność z systemami komunikacji zdalnej w wersji 2.0, należy przeprowadzić migrację całej usługi WCF. Migracja z wywołaniem funkcji zdalnych .NET w wersji 2.0 do programu WCF wymaga wprowadzenia zmian do obiektu zdalnego interfejsu i jego ustawienia konfiguracji. Oba te tematy zostały uwzględnione w [z wywołaniem funkcji zdalnych do programu Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie pojęć](../../../../docs/framework/wcf/conceptual-overview.md)
