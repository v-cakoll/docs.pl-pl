---
title: Wprowadzenie do rozszerzalności
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 331e71f26b1c703f7df27086d943e799b4eb13e2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="introduction-to-extensibility"></a>Wprowadzenie do rozszerzalności
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Model aplikacji jest zaprojektowana w celu rozwiązania większa część wymaganiach dotyczących komunikacji z dowolnej aplikacji rozproszonej. Zawsze jednak mogą scenariusze, które nie obsługują implementacji dostarczane przez system i domyślny model aplikacji. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Modelu rozszerzalności jest przeznaczona do obsługi niestandardowych scenariuszy, umożliwiając zmodyfikować zachowanie systemu na każdym poziomie, nawet do punktu wymiana modelu całej aplikacji. W tym temacie opisano różne obszary rozszerzenia i wskazuje więcej informacji o poszczególnych.  
  
## <a name="areas-to-extend"></a>Obszarów, aby rozszerzyć  
 Można rozszerzyć:  
  
-   Środowisko uruchomieniowe aplikacji. Spowoduje to rozszerzenie, wysyłki i przetwarzanie komunikatów dla aplikacji. Ten obszar obejmuje również rozszerzenie systemu zabezpieczeń, system metadanych systemu serializacji i powiązania i elementów, które połączyć aplikację z podstawowym systemie kanału wiązania.  
  
-   Kanał i środowiska uruchomieniowego kanału. Rozszerza to system, który działa na poziomie komunikatu, protokół, transport i obsługa kodowania.  
  
-   Środowisko uruchomieniowe hosta. Spowoduje to rozszerzenie relacji hostingu domeny aplikacji do środowiska wykonawczego kanału i aplikacji.  
  
### <a name="extending-the-application-runtime"></a>Rozszerzanie środowiska uruchomieniowego aplikacji  
 W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji, jest różnica między wiadomości, które są przeznaczone dla odpowiedniego kanału i komunikaty, które są przeznaczone dla aplikacji. Komunikaty z kanałów obsługuje niektóre funkcje związane z kanału, takie jak ustanawianie bezpiecznej konwersacji lub ustanawiania niezawodnej sesji. Komunikaty te nie są dostępne do środowiska wykonawczego aplikacji; są przetwarzane przed uczestniczy warstwy aplikacji.  
  
 Komunikatów aplikacji zawiera dane, które jest przeznaczone dla klienta lub operacji usługi, utworzony zostanie lub klienta. Komunikaty te są dostępne dla systemu rozszerzenia na poziomie aplikacji w formie wiadomości lub obiektu, w zależności od potrzeb.  
  
 Wszystkie komunikaty przechodzą przez system kanału; tylko komunikaty aplikacji są przekazywane z systemu kanału do aplikacji. Aby utworzyć nowe funkcje na poziomie kanału, muszą być rozszerzane systemu kanału. Aby utworzyć nowe funkcje na poziomie aplikacji, należy rozszerzyć środowiska uruchomieniowego usługi lub klienta (dystrybucja i fabryk kanałów, odpowiednio). [!INCLUDE[crabout](../../../includes/crabout-md.md)] rozszerzanie środowiska uruchomieniowego aplikacji, zobacz [rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Rozszerzanie zabezpieczeń  
 Aby utworzyć mechanizmy zabezpieczeń niestandardowych, takich jak tokeny i poświadczeń, będzie konieczne rozszerzenie systemu zabezpieczeń. Aby uzyskać więcej informacji, zobacz [rozszerzanie zabezpieczeń](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Rozszerzanie metadanych  
 Do udostępnienia metadanych w inny sposób niż domyślna, należy rozszerzyć system metadanych. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu metadanych](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Rozszerzenie serializacji  
 Aby utworzyć niestandardowe kodery, podaj surogatów danych lub inne zadania dotyczące dostosowywania przeniesionych danych, należy rozszerzyć system serializacji. Aby uzyskać więcej informacji, zobacz [rozszerzanie koderów i serializatorów](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Rozszerzanie powiązań  
 Aby skojarzyć kanały transportu lub protokołu z warstwy aplikacji, należy rozszerzyć system powiązania. Aby uzyskać więcej informacji, zobacz [rozszerzanie powiązań](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Rozszerzanie systemu kanału  
 Do tworzenia kanałów, które obsługują niestandardowe transportu lub protokołu funkcji, zobacz [rozszerzanie warstwy kanału](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Rozszerzanie usługę hostingu systemu  
 Aby zmodyfikować model aplikacji obejmujących całą usługę, należy rozszerzyć <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> klasy. Aby uzyskać więcej informacji, zobacz [rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Aby zmodyfikować relację hostingu domeny aplikacji hosta usługi, należy rozszerzyć <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> klasy. Aby uzyskać więcej informacji, zobacz [rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie architektury WCF](../../../docs/framework/wcf/extending/index.md)
