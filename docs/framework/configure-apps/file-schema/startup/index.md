---
title: Schemat ustawień uruchamiania
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 59f0441b79244eb529be338495c32af886a5f2b3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="startup-settings-schema"></a>Schemat ustawień uruchamiania
Ustawienia uruchamiania Określ wersję środowiska CLR, które należy uruchomić aplikację.  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Określa, czy aplikacja obsługuje tylko wersję 1.0 środowisko uruchomieniowe języka wspólnego. Należy użyć aplikacji skompilowanej za pomocą środowiska wykonawczego w wersji 1.1  **\<supportedRuntime >** elementu.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|  
|[\<Uruchamianie >](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Zawiera  **\<requiredRuntime >** i  **\<supportedRuntime >** elementów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Określanie wersji środowiska uruchomieniowego do użycia](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
