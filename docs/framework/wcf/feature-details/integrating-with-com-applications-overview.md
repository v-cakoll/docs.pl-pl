---
title: Przegląd integrowania z aplikacjami modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: c789d4a52da9b2785fb5919a674bf19f23d23509
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493399"
---
# <a name="integrating-with-com-applications-overview"></a>Przegląd integrowania z aplikacjami modelu COM
Windows Communication Foundation (WCF) zapewnia dewelopera kodu zarządzanego przy użyciu bogate środowisko tworzenia połączonych aplikacji. Jednak jeśli masz znaczących inwestycji w niezarządzanym kodzie oparte na modelu COM i nie chcesz migrować, można nadal zintegrować usług sieci Web WCF bezpośrednio z istniejącego kodu za pomocą moniker usługi WCF. Krótka nazwa usługi może służyć w środowiskach programistycznych szeroki zakres modelu COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.  
  
> [!NOTE]
>  Moniker usługi używa kanał komunikacyjny WCF dla całej komunikacji. Bezpieczeństwo i tożsamość mechanizmów dla tego kanału różnią się od używanych w standardowe COM i DCOM serwera proxy. Ponadto ponieważ moniker usługi używa kanał komunikacyjny WCF domyślny limit czasu jest jedną minutę na wszystkich wywołań.  
  
 Moniker usługi jest używany z `GetObject` funkcji niezarządzanej developer podejścia jednoznacznie, specyficzne dla modelu COM przy wywoływania usługi sieci Web WCF. Wymaga lokalnego, widoczny dla modelu COM definicja kontraktu usługi WCF w sieci Web i powiązania, który ma być używany. Podobnie jak innymi klientami WCF moniker usługi należy tworzyć typu kanału do usługi, chociaż tej konstrukcji kanału wykonywane w sposób przezroczysty dla programisty modelu COM przy pierwszym wywołaniu metody.  
  
 Wspólne innych klienci WCF, korzystając z monikerem aplikacje Określ address, binding i contract do komunikowania się z usługą. Kontrakt można określić w jednym z następujących sposobów:  
  
-   Typu kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.  
  
-   Kontrakt WSDL — Umowa jest dostarczany w formie dokument WSDL.  
  
-   MEX kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Parametry obsługiwane przez Moniker usługi  
 W poniższej tabeli przedstawiono parametry, które są obsługiwane przez moniker usługi.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`address`|Adres URL lokalizacji usługi.|  
|`binding`|Nazwa sekcji powiązania z konfiguracji aplikacji.|  
|`bindingConfiguration`|Nazwane wystąpienie obiektu binding z wewnątrz sekcji powiązania o nazwie.|  
|`contract`|Identyfikator interfejsu (IID) reprezentujący kontrakt usługi lub Nazwa kontraktu (od MEX).|  
|`wsdl`|Dokument WSDL, który zapewnia alternatywny definicję kontraktu.|  
|`spnIdentity`|Tożsamość główna nazwa (usługi SPN) serwera używanego do komunikacji z usługą.|  
|`upnIdentity`|Tożsamość główna nazwa (UPN) użytkownika ma być używany do komunikacji z usługą.|  
|`dnsIdentity`|Tożsamość DNS ma być używany do komunikacji z usługą.|  
|`mexAddress`|Adres URL lokalizacji punktu końcowego usługi wymiany metadanych (MEX).|  
|`mexBinding`|Nazwa sekcji powiązania z konfigurację aplikacji, aby połączyć się z punktem końcowym MEX.|  
|`mexBindingConfiguration`|Nazwane wystąpienie obiektu binding z wewnątrz sekcji powiązania o nazwie nawiązywania połączenia z punktem końcowym MEX.|  
|`bindingNamespace`|Namespace nazwy sekcji powiązania z pobrane MEX.|  
|`contractNamespace`|Namespace umowy z pobrane MEX.|  
|`mexSpnIdentity`|Tożsamość główna nazwa (usługi SPN) serwera, które ma być używany do komunikacji z punktem końcowym MEX.|  
|`mexUpnIdentity`|Tożsamość główna nazwa (UPN) użytkownika ma być używany do komunikacji z punktem końcowym MEX.|  
|`mexDnsIdentity`|Tożsamość DNS ma być używany do komunikacji z punktem końcowym MEX.|  
|`serializer`|Określ użycie serializatora "xml" lub "datacontract".|  
  
> [!NOTE]
>  Nawet wtedy, gdy jest używany z klientami całkowicie oparty na modelu COM, moniker usługi wymaga WCF i obsługi .NET Framework 2.0, można zainstalować na komputerze klienckim. Jest również krytycznych, że aplikacje klienckie, które używają moniker usługi załadować odpowiednią wersję środowiska uruchomieniowego .NET Framework. Używając krótkiej nazwy w aplikacjach pakietu Office, aby upewnić się, że jest załadowany poprawne framework w wersji może wymagać pliku konfiguracji. Na przykład przy użyciu programu Excel, następujący tekst należy umieścić w pliku o nazwie Excel.exe.config w tym samym katalogu co plik Excel.exe:  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: rejestrowanie i konfigurowanie monikera usługi](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
