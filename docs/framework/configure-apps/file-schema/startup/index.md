---
title: "Schemat ustawień uruchamiania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f344139fd7d7c84aa75ab5e17b6312f3b0c3e031
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="startup-settings-schema"></a>Schemat ustawień uruchamiania
Ustawienia uruchamiania Określ wersję środowiska CLR, które należy uruchomić aplikację.  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Określa, czy aplikacja obsługuje tylko wersję 1.0 środowisko uruchomieniowe języka wspólnego. Należy użyć aplikacji skompilowanej za pomocą środowiska wykonawczego w wersji 1.1  **\<supportedRuntime >** elementu.|  
|[\<supportedRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|Zawiera  **\<requiredRuntime >** i  **\<supportedRuntime >** elementów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Określanie wersji środowiska uruchomieniowego do użycia](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
