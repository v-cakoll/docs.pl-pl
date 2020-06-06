---
title: Schemat ustawień uruchamiania
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701518"
---
# <a name="startup-settings-schema"></a>Schemat ustawień uruchamiania

Ustawienia uruchamiania określają wersję środowiska uruchomieniowego języka wspólnego, która powinna uruchamiać aplikację.  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego. Aplikacje skompilowane przy użyciu środowiska uruchomieniowego w wersji 1,1 powinny używać **\<supportedRuntime>** elementu.|  
|[\<supportedRuntime>](supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|  
|[\<startup>](startup-element.md)|Zawiera **\<requiredRuntime>** elementy i **\<supportedRuntime>** .|  
  
## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
