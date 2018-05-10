---
title: Podstawowy cykl życia programowania
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: b20167ad776f3524e4516b71e43ab8cdb5c2aea4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="basic-programming-lifecycle"></a>Podstawowy cykl życia programowania
Windows Communication Foundation (WCF) umożliwia aplikacjom komunikowanie się, czy znajdują się na tym samym komputerze, przez Internet, lub na platformach inną aplikację. W tym temacie omówiono zadania, które są wymagane do tworzenia aplikacji WCF. Przykładową aplikację pracy, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Podstawowe zadania  
 Podstawowe zadania do wykonania znajdują się w kolejności:  
  
1.  Definiowanie kontraktu usługi. Kontrakt usługi Określa podpis usługi, danych, który wymienia i innych podstawie umowy wymaganych danych. Aby uzyskać więcej informacji, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Implementuje kontrakt. Aby zaimplementować kontrakt usługi, Utwórz klasę, która implementuje kontrakt i określ niestandardowe zachowania, które powinny mieć środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Skonfiguruj usługę, określając punktów końcowych i innych informacji o zachowanie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Host usługi. Aby uzyskać więcej informacji, zobacz [Hosting usług](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Tworzenie aplikacji klienckich. Aby uzyskać więcej informacji, zobacz [kompilowanie klientów](../../../docs/framework/wcf/building-clients.md).  
  
 Chociaż w tematach w tej sekcji należy wykonać to zamówienie, niektóre scenariusze nie są uruchamiane na początku. Na przykład jeśli chcesz skompilować klienta istniejące usługi, możesz uruchomić w kroku 5. Lub jeśli tworzysz usługi, który będzie używany przez inne osoby, możesz pominąć krok 5.  
  
 Po zapoznaniu się z projektowanie kontraktów usług, możesz przeczytać [wprowadzenie do rozszerzalności](../../../docs/framework/wcf/introduction-to-extensibility.md). Jeśli masz problemy z usługą, sprawdź [szybkiego startu WCF Rozwiązywanie problemów z](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) aby zobaczyć, czy inne osoby mają takie same lub podobne problemy.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
