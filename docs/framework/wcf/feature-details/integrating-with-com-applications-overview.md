---
title: "Przegląd integrowania z aplikacjami modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e995fc66a925cb0ebe272c9dceca1ba63b9459d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a>Przegląd integrowania z aplikacjami modelu COM
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]udostępnia bogate środowisko tworzenia połączonych aplikacji dewelopera kodu zarządzanego. Jednak jeśli masz znaczących inwestycji w niezarządzanym kodzie oparte na modelu COM i nie chcesz migrować, można nadal zintegrować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług sieci Web bezpośrednio do istniejącego kodu za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] krótkiej nazwy. Krótka nazwa usługi może służyć w środowiskach programistycznych szeroki zakres modelu COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.  
  
> [!NOTE]
>  Moniker usługi używa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanał komunikacyjny na potrzeby całej komunikacji. Bezpieczeństwo i tożsamość mechanizmów dla tego kanału różnią się od używanych w standardowe COM i DCOM serwera proxy. Ponadto ponieważ używa moniker usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanał komunikacyjny jedną minutę na wszystkich wywołań jest domyślny limit czasu.  
  
 Moniker usługi jest używany z `GetObject` funkcji niezarządzanej developer podejścia jednoznacznie, specyficzne dla modelu COM przy dotyczący wywołania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług sieci Web. Wymaga to definicji lokalnego, widoczny dla modelu COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt usługi i powiązania, który ma być używany w sieci Web. Takich jak inne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, moniker usługi należy tworzyć typu kanału do usługi, chociaż ten kanał konstrukcji wykonywane w sposób przezroczysty dla programisty modelu COM przy pierwszym wywołaniu metody.  
  
 Wspólne innych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, korzystając z krótką nazwę, aplikacje Określ address, binding i contract do komunikowania się z usługą. Kontrakt można określić w jednym z następujących sposobów:  
  
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
>  Nawet wtedy, gdy jest używany z klientami całkowicie oparty na modelu COM, wymaga moniker usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i obsługi .NET Framework 2.0 jest zainstalowany na komputerze klienckim. Jest również krytycznych, że aplikacje klienckie, które używają moniker usługi załadować odpowiednią wersję środowiska uruchomieniowego .NET Framework. Używając krótkiej nazwy w aplikacjach pakietu Office, aby upewnić się, że jest załadowany poprawne framework w wersji może wymagać pliku konfiguracji. Na przykład przy użyciu programu Excel, następujący tekst należy umieścić w pliku o nazwie Excel.exe.config w tym samym katalogu co plik Excel.exe:  
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
 [Porady: zarejestrować i skonfigurować krótkiej nazwy](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
