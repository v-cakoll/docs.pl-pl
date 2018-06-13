---
title: Hosting usług danych (usługi danych WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: d3adf45e0876ae63b111a53461eee9aeee519b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362853"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hosting usług danych (usługi danych WCF)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można utworzyć usługi, która opisuje dane jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych. Ta usługa danych jest zdefiniowany jako klasa, która dziedziczy <xref:System.Data.Services.DataService%601>. Ta klasa udostępnia funkcje wymagane do przetwarzania komunikatów żądań, przeprowadzania aktualizacji w źródle danych oraz do generowania wiadomości odpowiedzi, co jest wymagane przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Jednak usługa danych nie można powiązać i nasłuchiwania gniazda sieci dla przychodzących żądań HTTP. Dla tej funkcji wymagane usługi danych zależy od składnika hostingu.  
  
 Hosta usługi danych wykonuje następujące zadania w imieniu usług danych:  
  
-   Nasłuchuje żądań i kieruje te żądania do usługi danych.  
  
-   Tworzy wystąpienie usługi danych dla każdego żądania.  
  
-   Żądania przez usługę danych procesów żądania przychodzącego.  
  
-   Wysyła odpowiedź w imieniu usług danych.  
  
 Aby uprościć hosting usług danych, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] został zaprojektowany do integrowania z usługi Windows Communication Foundation (WCF). Usługi danych udostępnia domyślną implementację WCF, która służy jako hosta usługi danych w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji. W związku z tym można hosta usługi danych w jednym z następujących sposobów:  
  
-   W [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
-   W zarządzanej aplikacji obsługującej usługi hostowania samoobsługowego WCF.  
  
-   W niektórych innych niestandardowych hosta usługi danych.  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hosting w aplikacji ASP.NET usługi danych  
 Jeśli używasz **Dodaj nowy element** okna dialogowego w programie Visual Studio, aby zdefiniować usługę danych w aplikacji ASP.NET, narzędzie wygeneruje dwa nowe pliki w projekcie. Pierwszy plik ma `.svc` rozszerzenia i powoduje, że środowisko uruchomieniowe WCF sposobu utworzenia wystąpienia usługi danych. Poniżej przedstawiono przykład tego pliku w usłudze danych Northwind próbki utworzone po zakończeniu [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 Ta dyrektywa określa, że aplikacją w celu utworzenia hosta usługi danych o podanej nazwie klasy usługi za pomocą <xref:System.Data.Services.DataServiceHostFactory> klasy.  
  
 Na stronie CodeBehind `.svc` plik zawiera klasę, która jest implementacją usługi data, zdefiniowanego w następujący sposób dla usługi danych Northwind próbki:  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 Ponieważ usługa danych zachowuje się jak usługi WCF, Usługa danych integruje się z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i jest zgodna z modelem programowania sieci Web WCF. Aby uzyskać więcej informacji, zobacz [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) i [modelu programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## <a name="self-hosted-wcf-services"></a>Usług hostowania samoobsługowego WCF  
 Ponieważ zawiera implementacji programu WCF [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje hostingu samodzielnego usługi danych jako usługa WCF. Usługa może być własnym hostowanej w żadnym [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji, takich jak aplikacji konsoli. <xref:System.Data.Services.DataServiceHost> Klasy, która dziedziczy <xref:System.ServiceModel.Web.WebServiceHost>, jest używany do utworzenia wystąpienia usługi data pod określonym adresem.  
  
 Hostingu samodzielnego może służyć do projektowania i testowania, ponieważ jego ułatwia wdrażanie i rozwiązywanie problemów z usługi. Jednak tego rodzaju hosting nie zapewnia zaawansowane funkcje obsługi i zarządzania oferowane przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] lub przez Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [Hosting w zarządzanej aplikacji](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
## <a name="defining-a-custom-data-service-host"></a>Definiowanie hosta usługi danych niestandardowych  
 W przypadkach, w którym implementacja hosta programu WCF jest zbyt restrykcyjna również możliwość definiowania niestandardowych hosta usługi danych. Każda klasa implementująca <xref:System.Data.Services.IDataServiceHost> interfejs może służyć jako hosta usługi danych. Niestandardowy host musi implementować <xref:System.Data.Services.IDataServiceHost> interfejsu i mieć możliwość obsługi podstawowych obowiązków hosta usługi danych:  
  
-   Ścieżka katalogu głównego usługi udostępnić usługę danych.  
  
-   Przetworzyć informacji nagłówki żądań i odpowiedzi do odpowiedniego <xref:System.Data.Services.IDataServiceHost> implementacja elementu członkowskiego.  
  
-   Obsługa wyjątków zgłaszanych przez usługę danych.  
  
-   Sprawdź poprawność parametrów w ciągu zapytania.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Udostępnianie danych jako usługi](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
