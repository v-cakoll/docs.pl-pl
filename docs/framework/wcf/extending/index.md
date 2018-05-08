---
title: Rozszerzanie architektury WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 4990f14178551d9dccaca0f2899d8dbc4416cdc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="extending-wcf"></a>Rozszerzanie architektury WCF
Windows Communication Foundation (WCF) służy do modyfikowania i rozszerzania składników dokładnie określić czas wykonywania, a rozszerzenie aplikacji usługi. Przejdź w tematach w tej sekcji szczegółowo o architekturze rozszerzalności. Aby uzyskać więcej informacji na temat podstawy programowania, zobacz [podstawowe programowania WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 Warstwy modelu usług jest odpowiedzialny za ściąganie wiadomości przychodzących poza podstawowej kanały, tłumaczenia je do wywołania metody w kodzie aplikacji i wysłaniem wyniki z powrotem do wywołującego.  Rozszerzenia modelu usługi zmodyfikować, lub zaimplementuj wykonywania lub zachowanie komunikacji i funkcje dotyczące funkcji dyspozytora, niestandardowe zachowania, wiadomości i przechwytywaniu parametru i innych funkcji rozszerzalności.  
  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 Powiązania są obiekty, które opisują szczegóły komunikacji wymagane do połączenia z punktem końcowym. Powiązania niestandardowe lub rozszerzenia powiązania implementowania niestandardowych komunikacji wymagane do obsługi funkcji aplikacji.  
  
 [Rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 Warstwie kanału znajduje się poniżej warstwy modelu usług i jest odpowiedzialny za wymiana wiadomości między klientami i usługami. Rozszerzenia kanału można zaimplementować nowych funkcji protokołu, takie jak zabezpieczeń. Rozszerzenia kanał transportu również funkcje, takie jak wdrażanie nowego transportu sieciowego do przenoszenia wiadomości SOAP.  
  
 [Rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md)  
 Zabezpieczenia w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składa się z zabezpieczeń transfer (integralności, poufność i uwierzytelnianie), kontrola dostępu (autoryzacja) i inspekcji. Znaleziono klas w `IdentityModel` przestrzeni nazw są używane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do kontroli dostępu. Omówienie architektury zabezpieczeń służy do tworzenia niestandardowych oświadczenia, aby pomieścić systemów kontroli dostępu niestandardowych.  
  
 [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System metadanych to grupa klasy i interfejsy, które reprezentują metadane wymagane do wdrożenia aplikacji usługi. Modyfikowanie lub rozszerzyć klasy lub wdrożenia i skonfigurować interfejsów, aby wyeksportować i zaimportować niestandardowy metadane, takie jak rozszerzenia usługi sieci Web Services Description Language (WSDL) lub niestandardowych asercji WS PolicyAttachments.  
  
 [Rozszerzanie koderów i serializatorów](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 Koderów i serializatorów tłumaczenie danych z jednego formularza. Tematy w tej sekcji omówiono sposób rozszerzyć klasy dostarczony, aby spełnić te wymagania.  
  
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
