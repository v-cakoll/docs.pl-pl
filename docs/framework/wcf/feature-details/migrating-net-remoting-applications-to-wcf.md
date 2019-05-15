---
title: Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: c0ce7c9badc8bad6eedc58827b6efe2595ab2cf8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592867"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
**Ten temat dotyczy technologią starszą, która została zachowana na potrzeby zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecane w przypadku nowych wdrożeń. Teraz należy opracować aplikacje rozproszone przy użyciu usługi WCF.**  
  
 Istnieją dwa sposoby, aby móc korzystać z usługi WCF z istniejącymi aplikacjami wywołaniem funkcji zdalnych .NET: integracji i migracji. Integracja umożliwia wywołaniem funkcji zdalnych .NET w wersji 2.0 i usługi WCF działa obok siebie, co pozwala na udostępnianie tych samych obiektów firmy za pośrednictwem obie technologie jednocześnie bez konieczności modyfikowania istniejącego kodu wywołaniem funkcji zdalnych .NET w wersji 2.0. Integracja wymaga, że są uruchomione na .NET Framework 2.0 lub nowszej. Jeśli chcesz korzystać z funkcji WCF i nie ma potrzeby o komunikacji sieciowej zgodność z systemami komunikacji zdalnej w wersji 2.0, należy przeprowadzić migrację całej usługi WCF. Migracja z wywołaniem funkcji zdalnych .NET w wersji 2.0 do programu WCF wymaga wprowadzenia zmian do obiektu zdalnego interfejsu i jego ustawienia konfiguracji. Oba te tematy zostały uwzględnione w [z wywołaniem funkcji zdalnych do programu Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie pojęć](../../../../docs/framework/wcf/conceptual-overview.md)
