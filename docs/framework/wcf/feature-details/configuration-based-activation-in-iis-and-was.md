---
title: Aktywacja oparta na konfiguracji w usługach IIS i WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: da98d237c066b70398d3238a75500e8a3abbe887
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46531694"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Aktywacja oparta na konfiguracji w usługach IIS i WAS

Zwykle w przypadku hostowania usługi Windows Communication Foundation (WCF) w ramach usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS), musisz podać plik .svc. Plik .svc zawiera nazwę usługi i opcjonalne niestandardowe usługi fabryka hostów. Ten dodatkowy plik zwiększa możliwości zarządzania obciążenia. Funkcja aktywacja oparta na konfiguracji usuwa wymóg posiadania plików .svc i w związku z tym skojarzone obciążenie.

## <a name="configuration-based-activation"></a>Aktywacja oparta na konfiguracji

Aktywacja oparta na konfiguracji ma metadanych, które umożliwiają można umieścić w pliku svc i umieszcza je w pliku Web.config. W ramach <`serviceHostingEnvironment`> istnieje element <`serviceActivations`> element. W ramach <`serviceActivations`> elementu są co najmniej jeden <`add`> elementy, po jednym dla każdej usługi hostowanej. <`add`> Element zawiera atrybuty, które pozwalają na ustawienie adres względny dla usługi i typ usługi lub fabryki hostów usług. Konfiguracja poniższy przykład kodu pokazuje, jak jest używana w tej sekcji.

> [!NOTE]
>  Każdy <`add`> element musi określać, usługi lub atrybut fabryki. Określenie zarówno usługi fabryki dla atrybutów i jest dozwolone.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 Dzięki temu w pliku Web.config można umieścić kod źródłowy usługi w katalogu App_Code skompilowane zestawów w katalogu Bin aplikacji lub aplikacji.

> [!NOTE]
> - Korzystając z aktywacji opartej na konfigurację, wbudowany kod w plikach plików SVC nie jest obsługiwana.
> - `relativeAddress` Atrybutu musi być równa adresu względnego takich jak "\<podkatalogu > / service.svc" lub "~ /\<podrzędnych directory/service.svc".
> - Wyjątek konfiguracji jest generowany, jeśli rejestrowanie adres względny, który nie ma znanym rozszerzeniem skojarzonych z programem WCF.
> - To adres względny określona względem katalogu głównego aplikacji wirtualnej.
> - Z powodu hierarchiczny model konfiguracji zarejestrowanych względnych adresów na poziomie maszyny i lokacji są dziedziczone przez aplikacje wirtualne.
> - Rejestracje w pliku konfiguracyjnym mają pierwszeństwo przed ustawieniami w .svc, .xamlx, xoml lub inny plik.
> - Wszelkie ' \' (ukośników odwrotnych) w identyfikatorze URI wysyłane do usług IIS / WAS są automatycznie konwertowane na "/" (ukośnik). Jeśli dodawany jest względna adres, który zawiera "\" i wysyłać identyfikator URI, który korzysta z adresu względnego usług IIS, ukośnik odwrotny jest konwertowany na ukośnik i usług IIS nie odpowiada on na adres względny. Usługi IIS wysyła informacje o śledzeniu, która wskazuje, że nie znaleziono dopasowań.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)
- [Przegląd hostowania usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)