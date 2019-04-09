---
title: Przegląd integrowania z aplikacjami modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 182e5f41498d8f5e3fcbc4b84aa7e86b67ce3ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087628"
---
# <a name="integrating-with-com-applications-overview"></a>Przegląd integrowania z aplikacjami modelu COM
Windows Communication Foundation (WCF) zapewnia dewelopera kodu zarządzanego przy użyciu bogate środowisko tworzenia połączonych aplikacji. Jednak jeśli masz znaczne inwestycje w niezarządzanym kodzie opartym na modelu COM i nie chcesz migrować, można nadal zintegrować usług sieci Web WCF bezpośrednio do istniejącego kodu przy użyciu monikera programu WCF. Moniker usługi może służyć w środowiskach programistycznych szeroki zakres COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.  
  
> [!NOTE]
>  Moniker usługi używa kanał komunikacyjny WCF dla całej komunikacji. Mechanizmy zabezpieczeń i tożsamości dla tego kanału różnią się od tych używanych w standardowych serwerów proxy modelu COM i DCOM. Ponadto ponieważ monikera programu używa kanał komunikacyjny WCF domyślny limit czasu jest jedną minutę na wszystkich wywołań.  
  
 Moniker usługi jest używana z `GetObject` funkcji niezarządzanych deweloperów dzięki podejściu silnie typizowane, specyficzne dla modelu COM do wywoływania usług sieci Web WCF. Wymaga to lokalne, widoczne dla modelu COM definicję kontraktu usługi WCF w sieci Web i powiązania, który ma być używany. Podobnie jak inni klienci WCF monikera programu należy tworzyć wpisane kanału do usługi, chociaż tej konstrukcji kanału wykonywane w sposób przezroczysty do programisty należy COM przy pierwszym wywołaniu metody.  
  
 Wspólnych innych WCF klientów, gdy używanie monikera programu aplikacje, określ adres, powiązania i umowy do komunikowania się z usługą. Kontrakt można określić w jednym z następujących sposobów:  
  
-   Wpisane kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.  
  
-   WSDL kontraktu — jest dostarczany w formie dokumentu WSDL.  
  
-   MEX kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Parametrów obsługiwanych przez monikera usługi  
 W poniższej tabeli przedstawiono parametry, które są obsługiwane przez monikera programu.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`address`|Lokalizacja adresu URL usługi.|  
|`binding`|Nazwa sekcji do powiązania z konfiguracji aplikacji.|  
|`bindingConfiguration`|Nazwane wystąpienie obiektu binding z wewnątrz sekcji o nazwie powiązania.|  
|`contract`|Identyfikator interfejsu (IID) reprezentujący kontraktu usługi lub Nazwa kontraktu (z MEX).|  
|`wsdl`|Dokument WSDL, który dostarcza alternatywnej formy definicję kontraktu.|  
|`spnIdentity`|Tożsamość główna nazwa (usługi SPN) serwera ma być używany do komunikacji z usługą.|  
|`upnIdentity`|Tożsamość głównej nazwy (UPN) użytkownika, które ma być używany do komunikacji z usługą.|  
|`dnsIdentity`|Tożsamość DNS, który ma być używany do komunikacji z usługą.|  
|`mexAddress`|Lokalizacja adresu URL punktu końcowego metadanych programu Exchange (MEX) usługi.|  
|`mexBinding`|Powiązania nazwy sekcji z konfiguracji aplikacji, aby połączyć się z punktem końcowym MEX.|  
|`mexBindingConfiguration`|Nazwane wystąpienie obiektu binding z w ramach sekcji powiązania o nazwie, aby połączyć się z punktem końcowym MEX.|  
|`bindingNamespace`|Namespace nazwa sekcji powiązania z pobrane MEX.|  
|`contractNamespace`|Namespace umowy z pobrane MEX.|  
|`mexSpnIdentity`|Tożsamość główna nazwa (usługi SPN) serwera ma być używany do komunikowania się z punktem końcowym MEX.|  
|`mexUpnIdentity`|Tożsamość głównej nazwy (UPN) użytkownika, które ma być używany do komunikowania się z punktem końcowym MEX.|  
|`mexDnsIdentity`|Tożsamość DNS, który ma być używany do komunikowania się z punktem końcowym MEX.|  
|`serializer`|Określ korzystanie z serializatora "xml" lub "schematu datacontract".|  
  
> [!NOTE]
>  Nawet wtedy, gdy jest używany z klientami w całości opartą na modelu COM, monikera programu wymaga usług WCF i pomocnicze systemu .NET Framework 2.0, należy zainstalować na komputerze klienckim. Jest również krytycznych, że aplikacje klienckie, które używają monikera programu ładować odpowiednią wersję środowiska uruchomieniowego .NET Framework. Korzystając z monikerem w aplikacjach pakietu Office, plik konfiguracji może być wymagane, aby zapewnić, że jest załadowany poprawną wersję. Na przykład za pomocą programu Excel, następujący tekst będzie umieszczona w pliku o nazwie Excel.exe.config w tym samym katalogu co plik Excel.exe:  
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
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: rejestrowanie i konfigurowanie krótkiej nazwy usługi](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
