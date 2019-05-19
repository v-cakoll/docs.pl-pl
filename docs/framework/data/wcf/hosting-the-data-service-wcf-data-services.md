---
title: Hosting usługi danych (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: c240a76ea54d57456ff13fee7a48981354f669de
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881273"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hosting usługi danych (WCF Data Services)
Korzystając z usług danych WCF, można utworzyć usługę, która udostępnia dane jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych. Ta usługa danych jest zdefiniowany jako klasę, która dziedziczy z <xref:System.Data.Services.DataService%601>. Ta klasa udostępnia funkcje wymagane do przetwarzania komunikatów żądań, przeprowadzania aktualizacji względem źródła danych i generowanie wiadomości odpowiedzi, zgodnie z wymaganiami protokołu OData. Jednak usługa danych nie można powiązać i nasłuchiwanie przychodzących żądań HTTP na gnieździe sieci. Dla tej funkcji wymagane usługi danych opiera się na składniku hostingowych.

 Host usługi danych wykonuje następujące zadania w imieniu usługi danych:

- Nasłuchuje żądań i kieruje żądania do usługi danych.

- Tworzy wystąpienie usługi danych dla każdego żądania.

- Czy usługa danych przetwarzać żądania przychodzącego żądania.

- Wysyła odpowiedź w imieniu usługi danych.

 Aby uprościć hostująca usługę danych, usługi danych WCF został zaprojektowany do integrowania za pomocą programu Windows Communication Foundation (WCF). Usługa danych udostępnia domyślną implementację WCF, która służy jako hosta usługi danych w aplikacji ASP.NET. W związku z tym można hostować usługi danych w jednym z następujących sposobów:

- W aplikacji ASP.NET.

- W aplikacji zarządzanej, który obsługuje samodzielnie hostowanej usługi WCF.

- W niektórych innych niestandardowych danych hosta usługi.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hosting usługi danych w aplikacji ASP.NET

Kiedy używasz **Dodaj nowy element** okna dialogowego w programie Visual Studio 2015 do definiowania usługi danych w aplikacji ASP.NET, narzędzie generuje dwa nowe pliki w projekcie. Pierwszy plik ma `.svc` rozszerzenia i powoduje, że środowisko wykonawcze programu WCF sposobu tworzenia wystąpienia usługi danych. Oto przykład tego pliku do usługi danych Northwind przykładowe utworzone po zakończeniu [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Oznacza ona aplikacji do utworzenia hosta usługi dla klasy usługi danych o podanej nazwie za pomocą <xref:System.Data.Services.DataServiceHostFactory> klasy.

 Strona związanym z kodem `.svc` plik zawiera klasę, która jest implementacją usługi danych, która jest zdefiniowana w następujący sposób usługi Northwind przykładowe dane:

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 Ponieważ usługa danych zachowuje się jak usługi WCF, Usługa danych integruje się z programem ASP.NET i jest zgodna z modelu programowania w sieci Web WCF. Aby uzyskać więcej informacji, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) i [modelu programowania protokołu HTTP sieci Web programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).

## <a name="self-hosted-wcf-services"></a>Usług hostowania samoobsługowego WCF
 Ponieważ zawiera implementację usługi WCF, usług danych WCF obsługuje własnym hostująca usługę danych jako usługa WCF. Usługa może być samodzielnie hostowane w dowolnej aplikacji .NET Framework, takie jak aplikacja konsoli. <xref:System.Data.Services.DataServiceHost> Klasy, która dziedziczy po elemencie <xref:System.ServiceModel.Web.WebServiceHost>, jest używany do utworzenia wystąpienia usługi danych pod określonym adresem.

 Hostingu samodzielnego może służyć do tworzenia i testowania, ponieważ jego ułatwia wdrażanie i rozwiązywanie problemów z usługi. Jednak tego rodzaju hostingu nie zapewnia zaawansowane hostingu i funkcje zarządzania dostarczane przez platformę ASP.NET lub Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [hostowanie w aplikacji Managed](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Definiowanie hosta usługi danych niestandardowych
 W przypadkach, w których implementacja hosta usługi WCF jest zbyt restrykcyjne można również zdefiniować niestandardowy host usługi danych. Każda klasa implementująca <xref:System.Data.Services.IDataServiceHost> interfejs może służyć jako hosta sieci usługi danych. Niestandardowy host musi implementować <xref:System.Data.Services.IDataServiceHost> interfejs i obsługiwać następujące obowiązki podstawowe dane hosta usługi:

- Usługi danych należy udostępnić ścieżkę katalogu głównego usługi.

- Przetwarzania żądań i odpowiedzi informacji nagłówki do odpowiedniego <xref:System.Data.Services.IDataServiceHost> implementacji elementu członkowskiego.

- Obsługa wyjątków zgłaszanych przez usługę danych.

- Sprawdza poprawność parametrów ciągu zapytania.

## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Udostępnianie danych jako usługi](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
