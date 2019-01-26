---
title: Schemat ustawień uruchamiania
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083421"
---
# <a name="startup-settings-schema"></a>Schemat ustawień uruchamiania

Ustawienia uruchamiania określić wersję środowiska uruchomieniowego języka wspólnego, należy uruchomić aplikację.  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego. Skorzystaj z aplikacji utworzonych za pomocą środowiska uruchomieniowego wersji 1.1  **\<supportedRuntime >** elementu.|  
|[\<supportedRuntime>](supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|  
|[\<Uruchamianie >](startup-element.md)|Zawiera  **\<requiredRuntime >** i  **\<supportedRuntime >** elementów.|  
  
## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
