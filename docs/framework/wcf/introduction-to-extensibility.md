---
title: Wprowadzenie do rozszerzalności
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: ae820e88a790aeaad7c57cde2db84b8168f273a9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321052"
---
# <a name="introduction-to-extensibility"></a>Wprowadzenie do rozszerzalności
Model aplikacji Windows Communication Foundation (WCF) jest przeznaczony do rozwiązywania większej części wymagań komunikacji każdej aplikacji rozproszonej. Jednak zawsze istnieją scenariusze, które nie obsługują domyślnego modelu aplikacji i implementacji dostarczonych przez system. Model rozszerzalności WCF jest przeznaczony do obsługi niestandardowych scenariuszy przez umożliwienie modyfikacji zachowania systemu na każdym poziomie, nawet w przypadku zastąpienia całego modelu aplikacji. W tym temacie opisano różne obszary rozszerzenia i punkty dodatkowe informacje o każdej z nich.  
  
## <a name="areas-to-extend"></a>Obszary do rozszerania  
 Można zwiększyć:  
  
- Środowisko uruchomieniowe aplikacji. Rozszerza to wysyłanie i przetwarzanie komunikatów dla aplikacji. Ten obszar obejmuje również Rozszerzanie systemu zabezpieczeń, systemu metadanych, systemu serializacji oraz powiązań i elementów powiązania, które łączą aplikację z systemem kanałów bazowych.  
  
- Środowisko uruchomieniowe kanału i kanału. Rozszerza to system, który działa na poziomie komunikatu, zapewniając obsługę protokołów, transportu i kodowania.  
  
- Środowisko uruchomieniowe hosta. Rozszerza to relację domeny aplikacji hostingu do środowiska uruchomieniowego kanału i aplikacji.  
  
### <a name="extending-the-application-runtime"></a>Rozszerzanie środowiska uruchomieniowego aplikacji  
 W aplikacjach WCF istnieje rozróżnienie między komunikatami przeznaczonymi dla odpowiedniego kanału i wiadomości, które są przeznaczone dla samej aplikacji. Komunikaty kanału obsługują niektóre funkcje związane z kanałem, takie jak Ustanawianie bezpiecznej konwersacji lub Nawiązywanie niezawodnej sesji. Te komunikaty nie są dostępne dla środowiska uruchomieniowego aplikacji; są one przetwarzane przed przystąpieniem do warstwy aplikacji.  
  
 Komunikaty aplikacji zawierają dane, które są przeznaczone dla operacji klienta lub usługi utworzonych przez Ciebie lub przez klienta. Te komunikaty są dostępne dla systemu rozszerzenia poziomu aplikacji w formularzu komunikatów lub obiektów, w zależności od potrzeb.  
  
 Wszystkie komunikaty przechodzą przez system kanałów; tylko komunikaty aplikacji są przesyłane z systemu kanału do aplikacji. Aby utworzyć nowe funkcje poziomu kanału, należy rozłożyć system kanałów. Aby utworzyć nowe funkcje na poziomie aplikacji, należy najpierw zainstalować usługę lub środowisko uruchomieniowe klienta (odpowiednio odnowień oraz fabryki kanałów). Aby uzyskać więcej informacji na temat rozszerzania środowiska uruchomieniowego aplikacji, zobacz [Rozszerzanie elementu ServiceHost i warstwy modelu usług](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Rozszerzanie zabezpieczeń  
 Aby utworzyć niestandardowe mechanizmy zabezpieczeń, takie jak tokeny i poświadczenia, należy rozbudować system zabezpieczeń. Aby uzyskać więcej informacji, zobacz [rozszerzanie zabezpieczeń](./extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Rozszerzanie metadanych  
 Aby udostępnić metadane w sposób inny niż domyślny, należy zwiększyć system metadanych. Aby uzyskać więcej informacji, zobacz [Rozszerzanie systemu metadanych](./extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Rozszerzanie serializacji  
 W celu utworzenia koderów niestandardowych, zapewnienia surogatów danych lub innej pracy obejmującej dostosowanie transferowanych danych należy rozbudować system serializacji. Aby uzyskać więcej informacji, zobacz [rozszerzanie koderów i serializatorów](./extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Rozszerzanie powiązań  
 Aby skojarzyć transport lub kanały protokołu z warstwą aplikacji, należy rozszerzać system powiązań. Aby uzyskać więcej informacji, zobacz [Rozszerzanie powiązań](./extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Rozszerzanie systemu kanału  
 Aby utworzyć kanały obsługujące niestandardowe transporty lub funkcje protokołu, zobacz [Rozszerzanie warstwy kanału](./extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Rozszerzanie systemu hostingu usług  
 Aby zmodyfikować model aplikacji dla całej usługi, należy rozłożyć <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> klasy. Aby uzyskać więcej informacji, zobacz [Rozszerzanie elementu ServiceHost i warstwy modelu usług](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Aby zmodyfikować relację między domeną aplikacji hostingowej i hostem usługi, należy rozłożyć klasę <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Rozszerzanie hostingu przy użyciu obiektu ServiceHostFactory](./extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie architektury WCF](./extending/index.md)
