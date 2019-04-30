---
title: Rozszerzanie architektury WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 24ad74f04a3ac31d0b0d0d87f0d74f88c0521f50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768722"
---
# <a name="extending-wcf"></a>Rozszerzanie architektury WCF
Windows Communication Foundation (WCF) umożliwia modyfikowanie i Rozszerz składniki czasu wykonywania może precyzyjnie kontrolować i rozszerzanie aplikacji opartych na usługach. Przejdź w tematach w tej sekcji szczegółowo o architekturze rozszerzalności. Aby uzyskać więcej informacji na temat podstawy programowania zobacz [programowanie WCF Basic](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 Warstwy modelu usług jest odpowiedzialny za ściąganie komunikaty przychodzące poza podstawowym kanały, tłumaczenie je na wywołania metody w kodzie aplikacji i wyniki są wysyłane do obiektu wywołującego.  Rozszerzenia modelu usługi modyfikować ani implementować wykonywania lub zachowanie komunikacji i funkcje, obejmujące funkcje dyspozytora, niestandardowe zachowania, wiadomości i przejmowanie parametru i innych funkcji rozszerzalności.  
  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 Powiązania to obiekty, które opisują szczegółów komunikacji wymagane do połączenia z punktem końcowym. Powiązanie rozszerzenia lub powiązań niestandardowych implementacji komunikacji niestandardowe funkcje wymagane do obsługi funkcji aplikacji.  
  
 [Rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 Warstwy kanału znajduje się poniżej warstwy modelu usług i jest odpowiedzialny za wymiana wiadomości między klientami i usługami. Rozszerzenia kanału można zaimplementować nowych funkcji protokołu, takie jak zabezpieczenia. Rozszerzenia kanał transportu również funkcji, takich jak zaimplementowanie nowy transport do sieci, żeby komunikaty protokołu SOAP.  
  
 [Rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md)  
 Zabezpieczenia w programie WCF składa się z przeniesienia zabezpieczeń (integralności, poufności i uwierzytelnianie), kontrola dostępu (autoryzacja) i inspekcji. Klasy znalezione w `IdentityModel` przestrzeni nazw są używane przez architekturę WCF dla kontroli dostępu. Omówienie architektury zabezpieczeń pozwala na tworzenie niestandardowe typy oświadczeń do obsługi systemów kontroli dostępu niestandardowych.  
  
 [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 System metadanych WCF jest grupą klas i interfejsów, które reprezentują metadane wymagane do wdrożenia aplikacji opartych na usługach. Modyfikowanie lub rozszerzyć klasy lub wdrożyć i skonfigurować interfejsy, eksportowanie i importowanie niestandardowych metadanych, takich jak rozszerzenia usługi sieci Web Services Description Language (WSDL) lub niestandardowych asercji WS PolicyAttachments.  
  
 [Rozszerzanie koderów i serializatorów](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 Koderów i serializatorów wykonuje translację elementu danych z jednego formularza. Tematy w tej sekcji omówiono sposób rozszerzyć podanej klasy, aby spełnić te wymagania.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [Szczegóły funkcji WCF](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [Wskazówki i najlepsze rozwiązania](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
