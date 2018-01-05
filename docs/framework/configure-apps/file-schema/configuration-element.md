---
title: "&lt;Konfiguracja&gt; — element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3874a613879d099ede4968b5bce349aefa015a38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-element"></a>\<Konfiguracja > — element

Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.

**\<Konfiguracja >**

## <a name="syntax"></a>Składnia

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

Brak

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<assemblybinding — >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Określa zestaw powiązania zasad na poziomie konfiguracji.|
| [**\<Uruchamianie >** schemat ustawień](~/docs/framework/configure-apps/file-schema/startup/index.md) | Wszystkie elementy w schemat ustawień uruchamiania. |
| [**\<środowisko uruchomieniowe >** schemat ustawień](~/docs/framework/configure-apps/file-schema/runtime/index.md) | Wszystkie elementy w schemat ustawień środowiska uruchomieniowego. |
| [**\<System.Runtime.Remoting >** schemat ustawień](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | Wszystkie elementy w schemacie ustawień komunikacji zdalnej. |
| [**\<system.Net >** schemat ustawień](~/docs/framework/configure-apps/file-schema/network/index.md) | Wszystkie elementy w schemacie ustawień sieci. |
| [**\<cryptographysettings — >** schemat ustawień](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Wszystkie elementy w schemacie ustawień kryptograficznych. |
| [**\<Konfiguracja >** schemat sekcji](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Wszystkie elementy w schemacie ustawienia w sekcji konfiguracji. |
| [Schemat ustawień śledzenia i debugowania](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | Wszystkie elementy w schemacie ustawienia śledzenia i debugowania. |
| [Schemat ustawień konfiguracji programu ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx) | Wszystkie elementy w schemacie konfiguracji ASP.NET zawiera elementy dotyczące konfigurowania witryny sieci Web ASP.NET i aplikacji. Używane w *Web.config* plików. |
| [**\<< webServices >** schemat ustawień](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | Wszystkie elementy w schemacie ustawienia usług sieci Web. |
| [Schemat ustawień internetowych](~/docs/framework/configure-apps/file-schema/web/index.md) | Wszystkie elementy w schemat ustawień sieci Web, który zawiera elementy dotyczące konfigurowania, jak działa ASP.NET przy użyciu aplikacji hosta, takich jak IIS. Używane w *konfigurację aspnet.config* plików. |

## <a name="remarks"></a>Uwagi

Każdy plik konfiguracyjny musi zawierać dokładnie jeden  **\<konfiguracji >** elementu.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
