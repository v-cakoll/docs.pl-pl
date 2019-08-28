---
title: Przegląd integrowania z aplikacjami modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 99e3c2f4445673f3b74048a2b466203af7bc2795
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045881"
---
# <a name="integrating-with-com-applications-overview"></a>Przegląd integrowania z aplikacjami modelu COM

Windows Communication Foundation (WCF) udostępnia deweloperowi kodu zarządzanego zaawansowane środowisko do tworzenia połączonych aplikacji. Jeśli jednak masz znaczną inwestycję w niezarządzanym kodzie COM i nie chcesz migrować, nadal możesz zintegrować usługi sieci Web WCF bezpośrednio z istniejącym kodem przy użyciu monikera usługi WCF. Moniker usługi może być używany z szerokiego zakresu środowisk programistycznych opartych na modelu COM, takich jak Office VBA, Visual Basic 6,0 i Visual C++ 6,0.

> [!NOTE]
> Moniker usługi używa kanału komunikacyjnego WCF do całej komunikacji. Mechanizmy zabezpieczeń i tożsamości dla tego kanału różnią się od tych używanych w standardowych serwerach proxy modelu COM i modelu DCOM. Ponadto, ponieważ moniker usługi używa kanału komunikacyjnego WCF, domyślny okres limitu czasu wynosi jedną minutę dla wszystkich wywołań.

Moniker usługi jest używany z `GetObject` funkcją do zapewnienia niezarządzanego dewelopera z silnie wpisaną podejściem specyficznym dla modelu COM do wywoływania usług sieci Web WCF. Wymaga to lokalnej, widocznej dla modelu COM definicji kontraktu usługi sieci Web WCF i powiązania, które ma być używane. Podobnie jak w przypadku innych klientów programu WCF, moniker usługi musi utworzyć kanał o określonym typie dla usługi, chociaż konstrukcja tego kanału jest nieprzezroczysta dla programisty COM przy pierwszym wywołaniu metody.

Wspólnie z innymi klientami programu WCF przy użyciu monikera aplikacje określają adres, powiązanie i kontrakt do komunikacji z usługą. Umowę można określić w jeden z następujących sposobów:

- Typ kontraktu — kontrakt jest rejestrowany jako widoczny dla modelu COM na komputerze klienckim.

- Kontrakt WSDL — kontrakt jest dostarczany w formie dokumentu WSDL.

- Kontrakt MEX — umowa jest pobierana w czasie wykonywania z punktu końcowego wymiany metadanych (MEX).

## <a name="parameters-supported-by-the-service-moniker"></a>Parametry obsługiwane przez moniker usługi

W poniższej tabeli przedstawiono parametry, które są obsługiwane przez moniker usługi.

|Parametr|Opis|
|---------------|-----------------|
|`address`|Lokalizacja adresu URL usługi.|
|`binding`|Nazwa sekcji powiązania z konfiguracji aplikacji.|
|`bindingConfiguration`|Nazwane wystąpienie powiązania z poziomu sekcji nazwanego powiązania.|
|`contract`|Identyfikator interfejsu (IID) reprezentujący kontrakt usługi lub nazwę kontraktu (z MEX).|
|`wsdl`|Dokument WSDL, który zapewnia alternatywną formę definicji kontraktu.|
|`spnIdentity`|Tożsamość głównej nazwy serwera (SPN), która będzie używana do komunikacji z usługą.|
|`upnIdentity`|Tożsamość głównej nazwy użytkownika (UPN), która będzie używana do komunikacji z usługą.|
|`dnsIdentity`|Tożsamość DNS, która będzie używana do komunikacji z usługą.|
|`mexAddress`|Lokalizacja adresu URL punktu końcowego wymiany metadanych (MEX) usługi.|
|`mexBinding`|Nazwa sekcji powiązania z konfiguracji aplikacji w celu nawiązania połączenia z punktem końcowym MEX.|
|`mexBindingConfiguration`|Nazwane wystąpienie powiązania z poziomu sekcji nazwanego powiązania, aby nawiązać połączenie z punktem końcowym MEX.|
|`bindingNamespace`|Przestrzeń nazw sekcji powiązania z pobranej MEX.|
|`contractNamespace`|Przestrzeń nazw kontraktu z pobranej klasy MEX.|
|`mexSpnIdentity`|Tożsamość głównej nazwy serwera (SPN), która będzie używana do komunikacji z punktem końcowym MEX.|
|`mexUpnIdentity`|Tożsamość głównej nazwy użytkownika (UPN), która będzie używana do komunikacji z punktem końcowym MEX.|
|`mexDnsIdentity`|Tożsamość DNS, która będzie używana do komunikacji z punktem końcowym MEX.|
|`serializer`|Określ użycie serializatora "XML" lub "DataContract".|

> [!NOTE]
> W przypadku korzystania z całkowicie opartych na modelu COM moniker usługi wymaga programu WCF i .NET Framework 2,0 do zainstalowania na komputerze klienckim. Jest również ważne, aby aplikacje klienckie używające monikera usługi ładowały odpowiednią wersję środowiska uruchomieniowego .NET Framework. W przypadku używania monikera w aplikacjach pakietu Office może być wymagany plik konfiguracji, aby upewnić się, że załadowano poprawną wersję platformy. Na przykład w programie Excel następujący tekst powinien być umieszczony w pliku o nazwie Excel. exe. config w tym samym katalogu, w którym znajduje się plik Excel. exe:
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Rejestrowanie i Konfigurowanie monikera usługi](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
