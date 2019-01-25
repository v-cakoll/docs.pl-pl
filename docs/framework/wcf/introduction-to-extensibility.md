---
title: Wprowadzenie do rozszerzalności
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: 78a0410876016ef2d5249fe3b6a667cacc432320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654857"
---
# <a name="introduction-to-extensibility"></a>Wprowadzenie do rozszerzalności
Model aplikacji Windows Communication Foundation (WCF) jest przeznaczony do rozwiązywania większa część wymagania dotyczące komunikacji z dowolnej aplikacji rozproszonej. Jednak zawsze są scenariusze, które nie obsługują modelu aplikacji domyślnej i implementacje dostarczane przez system. Model rozszerzalności programu WCF jest przeznaczony do obsługi scenariuszy niestandardowych, dzięki któremu można zmodyfikować zachowanie systemu na każdym poziomie, nawet do punktu zamiany modelu całej aplikacji. W tym temacie opisano różne obszary rozszerzenia i wskazuje, aby uzyskać więcej informacji na temat każdego.  
  
## <a name="areas-to-extend"></a>Obszary, aby rozszerzyć  
 Możesz rozszerzyć:  
  
-   Czas wykonywania aplikacji. Spowoduje to rozszerzenie, wysyłanie i przetwarzanie komunikatów dla aplikacji. Ten obszar zawiera również rozszerzenie systemu zabezpieczeń, system metadanych, system serializacji i powiązania i powiązania elementy, które połączyć aplikację z podstawowym systemie kanału.  
  
-   Kanał i kanał w czasie wykonywania. Spowoduje to rozszerzenie system, który działa na poziomie komunikatu protokołu transportu, zapewniając i kodowanie pomocy technicznej.  
  
-   Środowisko uruchomieniowe hosta. Spowoduje to rozszerzenie relacji hostingu domeny aplikacji w środowisku uruchomieniowym kanału i aplikacji.  
  
### <a name="extending-the-application-runtime"></a>Rozszerzanie środowiska uruchomieniowego aplikacji  
 W aplikacji WCF jest rozróżnienie między wiadomości, które są przeznaczone do odpowiednich kanałów i komunikaty, które są przeznaczone dla samej aplikacji. Kanał wiadomości obsługuje niektóre funkcje związane z kanału, takie jak ustanawianie bezpiecznej konwersacji lub ustanawiania niezawodnych sesji. Te komunikaty nie są dostępne do środowiska uruchomieniowego aplikacji; są przetwarzane przed jest zaangażowana w warstwie aplikacji.  
  
 Komunikaty aplikacji zawierają danych, który jest przeznaczony dla klienta lub operacji usługi, który został utworzony użytkownik lub klienta. Te komunikaty są dostępne dla systemu rozszerzeń na poziomie aplikacji w postaci wiadomości lub obiekt, w zależności od potrzeb.  
  
 Wszystkie komunikaty przechodzą przez system kanału; tylko komunikaty z aplikacji są przekazywane z systemu kanału do aplikacji. Aby utworzyć nowe funkcje na poziomie kanału, można rozszerzyć system kanału. Aby utworzyć nowe funkcje na poziomie aplikacji, należy rozszerzyć środowisko uruchomieniowe usługi lub klienta (dystrybucja i fabryki kanałów, odpowiednio). Aby uzyskać więcej informacji na temat rozszerzania środowiska uruchomieniowego aplikacji, zobacz [rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Rozszerzanie zabezpieczeń  
 Aby skompilować mechanizmów zabezpieczeń niestandardowych, takich jak tokeny i poświadczeń, będzie konieczne rozszerzenie systemu zabezpieczeń. Aby uzyskać więcej informacji, zobacz [rozszerzanie zabezpieczeń](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Rozszerzanie metadanych  
 Aby udostępnić metadane w sposób inny niż domyślny, będzie konieczne rozszerzenie systemu metadanych. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu metadanych](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Rozszerzanie serializacji  
 Aby tworzyć niestandardowe kodery, podaj surogaty danych lub innych zadań dotyczących dostosowania przesłane dane, można rozszerzyć system serializacji. Aby uzyskać więcej informacji, zobacz [rozszerzanie koderów i serializatorów](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Rozszerzanie powiązań  
 Aby skojarzyć kanały transportu lub protokołu z warstwy aplikacji, można rozszerzyć system powiązań. Aby uzyskać więcej informacji, zobacz [rozszerzanie powiązań](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Rozszerzanie systemu kanału  
 Aby tworzyć kanały, które obsługują transportów niestandardowych lub protokołu funkcji, zobacz [rozszerzanie warstwy kanału](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Rozszerzanie usług obsługującego systemu  
 Aby zmodyfikować model aplikacji obejmujących całą usługę, należy rozszerzyć <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> klasy. Aby uzyskać więcej informacji, zobacz [rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Aby zmodyfikować relację hostingu domeny aplikacji hosta usługi, musisz rozszerzyć <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> klasy. Aby uzyskać więcej informacji, zobacz [rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Zobacz także
- [Rozszerzanie architektury WCF](../../../docs/framework/wcf/extending/index.md)
