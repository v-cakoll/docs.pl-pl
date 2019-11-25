---
title: Hostowanie usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 3abcd901bcb8a175aa6f30e53b142cbbde56a579
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975241"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hostowanie usługi danych (Usługi danych programu WCF)
Za pomocą Usługi danych programu WCF można utworzyć usługę, która udostępnia dane jako źródło danych protokołu typu Open Data Protocol (OData). Ta usługa danych jest definiowana jako Klasa, która dziedziczy po <xref:System.Data.Services.DataService%601>. Ta klasa udostępnia funkcje wymagane do przetwarzania komunikatów żądań, wykonywania aktualizacji względem źródła danych oraz generowania komunikatów odpowiedzi zgodnie z wymaganiami protokołu OData. Jednak usługa danych nie może powiązać się z gniazdem sieciowym i nasłuchiwać w nich w ramach przychodzących żądań HTTP. W przypadku tej wymaganej funkcji usługa danych opiera się na składniku hostingu.

 Host usługi danych wykonuje następujące zadania w imieniu usługi danych:

- Nasłuchuje żądań i kieruje je do usługi danych.

- Tworzy wystąpienie usługi danych dla każdego żądania.

- Żąda przetworzenia żądania przychodzącego przez usługę danych.

- Wysyła odpowiedź w imieniu usługi danych.

 Aby uprościć hosting usługi danych, Usługi danych programu WCF jest zaprojektowana do integracji z Windows Communication Foundation (WCF). Usługa danych zapewnia domyślną implementację programu WCF, która służy jako host usługi danych w aplikacji ASP.NET. W związku z tym usługa danych może być hostowana w jeden z następujących sposobów:

- W aplikacji ASP.NET.

- W zarządzanej aplikacji, która obsługuje samoobsługowe usługi WCF.

- W innym niestandardowym hoście usługi danych.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hosting usługi danych w aplikacji ASP.NET

W przypadku korzystania z okna dialogowego **Dodawanie nowego elementu** w programie Visual Studio 2015 w celu zdefiniowania usługi danych w aplikacji ASP.NET narzędzie generuje dwa nowe pliki w projekcie. Pierwszy plik ma `.svc` rozszerzenie i instruuje środowisko uruchomieniowe WCF, jak utworzyć wystąpienie usługi danych. Poniżej znajduje się przykład tego pliku dla usługi przykładowych danych Northwind utworzonych po zakończeniu [przewodnika Szybki Start](quickstart-wcf-data-services.md):

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Ta dyrektywa nakazuje aplikacji utworzenie hosta usługi dla nazwanej klasy usługi danych za pomocą klasy <xref:System.Data.Services.DataServiceHostFactory>.

 Strona Poprzednia kodu dla pliku `.svc` zawiera klasę, która jest implementacją samej usługi danych, która została zdefiniowana w następujący sposób dla przykładowej usługi danych Northwind:

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 Ponieważ usługa danych zachowuje się jak usługa WCF, usługa danych integruje się z usługą ASP.NET i jest zgodna z modelem programowania sieci Web w programie WCF. Aby uzyskać więcej informacji, zobacz model programowania [usług WCF i](../../wcf/feature-details/wcf-services-and-aspnet.md) [http w sieci Web](../../wcf/feature-details/wcf-web-http-programming-model.md)ASP.NET i WCF.

## <a name="self-hosted-wcf-services"></a>Samoobsługowe usługi WCF
 Ponieważ obejmuje implementację programu WCF, Usługi danych programu WCF obsługiwać samoobsługowego udostępniania usługi danych jako usługi WCF. Usługa może być samodzielna w dowolnej aplikacji .NET Framework, takiej jak Aplikacja konsolowa. Klasa <xref:System.Data.Services.DataServiceHost>, która dziedziczy po <xref:System.ServiceModel.Web.WebServiceHost>, jest używana do tworzenia wystąpienia usługi danych w określonym adresie.

 Funkcja samoobsługowego udostępniania może służyć do tworzenia i testowania, ponieważ ułatwia wdrażanie i rozwiązywanie problemów z usługą. Jednak ten rodzaj hostingu nie oferuje zaawansowanych funkcji hostingu i zarządzania udostępnianych przez ASP.NET lub przez Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [hosting w aplikacji zarządzanej](../../wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Definiowanie niestandardowego hosta usługi danych
 W przypadkach, w których implementacja hosta WCF jest zbyt restrykcyjna, można także zdefiniować hosta niestandardowego dla usługi danych. Każda klasa implementująca interfejs <xref:System.Data.Services.IDataServiceHost> może być używana jako host sieciowy usługi danych. Host niestandardowy musi implementować interfejs <xref:System.Data.Services.IDataServiceHost> i być w stanie obsłużyć następujące podstawowe obowiązki hosta usługi danych:

- Podaj usługę danych z ścieżką katalogu głównego usługi.

- Przetwarzaj informacje o nagłówkach żądań i odpowiedzi do odpowiedniej implementacji elementu członkowskiego <xref:System.Data.Services.IDataServiceHost>.

- Obsługa wyjątków zgłoszonych przez usługę danych.

- Sprawdź poprawność parametrów w ciągu zapytania.

## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Udostępnianie danych jako usługi](exposing-your-data-as-a-service-wcf-data-services.md)
- [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md)
