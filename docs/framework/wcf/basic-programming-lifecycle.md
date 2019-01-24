---
title: Podstawowy cykl życia programowania
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: d5322dfca1aa006ba2fc85b5dedebd09941f9c0e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499226"
---
# <a name="basic-programming-lifecycle"></a>Podstawowy cykl życia programowania
Windows Communication Foundation (WCF) umożliwia aplikacjom komunikowanie się, czy są one na tym samym komputerze w Internecie lub na platformach innej aplikacji. W tym temacie opisano zadania, które są wymagane do kompilowania aplikacji WCF. Pracy przykładowej aplikacji, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Podstawowe zadania  
 Podstawowe zadania do wykonania są w kolejności:  
  
1.  Definiowanie kontraktu usługi. Kontrakt usługi Określa podpis usługi, który wymienia dane i inne dane zobowiązana na mocy umowy wymagane. Aby uzyskać więcej informacji, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Zaimplementuj umowy. Implementowanie kontraktu usługi, utworzyć klasę, która implementuje ten kontrakt i określić niestandardowe zachowania, którzy powinni je posiadać środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Skonfiguruj usługę, określając punkty końcowe oraz inne informacje zachowanie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hostować usługę. Aby uzyskać więcej informacji, zobacz [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Tworzenie aplikacji klienckiej. Aby uzyskać więcej informacji, zobacz [kompilowanie klientów](../../../docs/framework/wcf/building-clients.md).  
  
 Mimo że tematy w tej sekcji należy wykonać to zamówienie, niektóre scenariusze nie są uruchamiane na początku. Na przykład jeśli chcesz skompilować klienta istniejące usługi, możesz rozpocząć od kroku 5. Lub jeśli opracowujesz usługi, które inni użytkownicy będą używać, możesz pominąć krok 5.  
  
 Gdy zaczynasz programować kontraktów usług, możesz przeczytać [wprowadzenie do rozszerzalności](../../../docs/framework/wcf/introduction-to-extensibility.md). Jeśli masz problemy z usługą, sprawdź [Szybki Start Rozwiązywanie problemów z architekturą WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) aby zobaczyć, czy inne osoby mają takie same lub podobne problemy.  
  
## <a name="see-also"></a>Zobacz także
- [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
