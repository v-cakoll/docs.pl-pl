---
title: Aktywacja oparta na konfiguracji w usługach IIS i WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 5e1672f4dd67950178c95d3e043e16072fcd0ef4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593584"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Aktywacja oparta na konfiguracji w usługach IIS i WAS

Zwykle podczas hostowania usługi Windows Communication Foundation (WCF) w ramach Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS) należy podać plik SVC. Plik SVC zawiera nazwę usługi i opcjonalną fabrykę hosta usługi niestandardowej. Ten dodatkowy plik dodaje obciążenie związane z zarządzaniem. Funkcja aktywacji opartej na konfiguracji eliminuje konieczność posiadania pliku svc i dlatego skojarzone obciążenie.

## <a name="configuration-based-activation"></a>Aktywacja oparta na konfiguracji

Aktywacja oparta na konfiguracji pobiera metadane, które były używane do umieszczania w pliku svc i umieszcza je w pliku Web. config. W<`serviceHostingEnvironment`> element zawiera <`serviceActivations`> elementu. W <`serviceActivations`> element to co najmniej jeden <`add`> elementów, po jednej dla każdej usługi hostowanej. `add`Element> <zawiera atrybuty pozwalające ustawić adres względny dla usługi i typu usługi lub fabryki hosta usługi. Poniższy przykładowy kod konfiguracji pokazuje, w jaki sposób ta sekcja jest używana.

> [!NOTE]
> Każdy `add` element> <musi określać usługę lub atrybut fabryki. Określanie atrybutów Service i Factory jest dozwolone.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 Za pomocą tego elementu w pliku Web. config można umieścić kod źródłowy usługi w katalogu App_Code aplikacji lub zgodnego zestawu w katalogu bin aplikacji.

> [!NOTE]
>
> - W przypadku korzystania z aktywacji opartej na konfiguracji, kod wbudowany w plikach. svc nie jest obsługiwany.
> - `relativeAddress`Atrybut musi być ustawiony na adres względny, taki jak " \<sub-directory> /Service.svc" lub "~/ \< Sub-Directory/Service. svc".
> - Wyjątek konfiguracji jest zgłaszany w przypadku zarejestrowania adresu względnego, który nie ma znanego rozszerzenia skojarzonego z WCF.
> - Określony adres względny jest względny w stosunku do elementu głównego aplikacji wirtualnej.
> - Ze względu na hierarchiczny model konfiguracji, zarejestrowane adresy względne na poziomie komputera i lokacji są dziedziczone przez aplikacje wirtualne.
> - Rejestracje w pliku konfiguracji mają pierwszeństwo przed ustawieniami w pliku SVC, xamlx, xoml lub innym.
> - Wszystkie znaki "\" (ukośniki odwrotne) w identyfikatorze URI wysłanym do usług IIS/były automatycznie konwertowane na znak "/" (ukośnik). Jeśli zostanie dodany adres względny, który zawiera znak "\", a w usługach IIS zostanie wysłany identyfikator URI, który używa adresu względnego, ukośnik odwrotny jest konwertowany na ukośnik, a usługi IIS nie będą zgodne z adresem względnym. Program IIS wysyła informacje śledzenia, które wskazują, że nie znaleziono dopasowań.

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Usługi hostingowe](../hosting-services.md)
- [Przegląd hostowania usług przepływu pracy](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
