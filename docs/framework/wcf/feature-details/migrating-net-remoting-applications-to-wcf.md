---
title: Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 1d7edab8ad89660f3384d0ccf556384175c4d5db
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212162"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrowanie aplikacji usług zdalnych platformy .NET do programu WCF
**Ten temat dotyczy starszej technologii, która jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami z istniejącymi aplikacjami i nie jest zalecana w przypadku nowych rozwiązań programistycznych. Aplikacje rozproszone powinny być teraz opracowywane przy użyciu programu WCF.**  
  
 Istnieją dwa sposoby wykorzystania programu WCF z istniejącymi aplikacjami zdalnymi platformy .NET: integrację i migrację. Funkcja integracji umożliwia udostępnianie tych samych obiektów firmowych w przypadku komunikacji zdalnej na platformie .NET 2,0 i WCF, co pozwala uwidocznić te same obiekty biznesowe w obu technologiach jednocześnie bez konieczności modyfikowania istniejącego kodu 2,0 komunikacji zdalnej dla platformy .NET. Integracja wymaga systemu na .NET Framework 2,0 lub nowszej. Jeśli chcesz korzystać z funkcji WCF i nie potrzebujesz zgodności sieci z usługami zdalnymi 2,0, możesz migrować całą usługę do platformy WCF. Migracja z usług zdalnej platformy .NET 2,0 do WCF wymaga wprowadzenia zmian w interfejsie zdalnego obiektu i jego ustawieniach konfiguracji. Oba te tematy zostały omówione w temacie [od usług zdalnych do Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie pojęć](../../../../docs/framework/wcf/conceptual-overview.md)
