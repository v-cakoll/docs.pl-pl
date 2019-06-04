---
title: <configuration>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 9a7b25c74763c020c0e19c3f6099db9001acf773
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705418"
---
# <a name="configuration-element"></a>\<Konfiguracja > element

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
| [ **\<assemblybinding — >** ](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Określa politykę powiązania zestawu na poziomie konfiguracji.|
| [ **\<Uruchamianie >** schemat ustawień](~/docs/framework/configure-apps/file-schema/startup/index.md) | Wszystkie elementy w schemacie ustawień uruchamiania. |
| [ **\<środowisko uruchomieniowe >** schemat ustawień](~/docs/framework/configure-apps/file-schema/runtime/index.md) | Wszystkie elementy w schemacie ustawień środowiska uruchomieniowego. |
| [ **\<System.Runtime.Remoting >** schemat ustawień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Wszystkie elementy w schemacie ustawień komunikacji zdalnej. |
| [ **\<system.Net>** Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) | Wszystkie elementy w schemacie ustawień sieci. |
| [ **\<cryptographySettings>** Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Wszystkie elementy w schemacie ustawień kryptograficznych. |
| [ **\<Konfiguracja >** schemat sekcji](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Wszystkie elementy w schemacie ustawień sekcji konfiguracji. |
| [Schemat ustawień śledzenia i debugowania](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | Wszystkie elementy w schemacie ustawień śledzenia i debugowania. |
| [Schemat ustawień konfiguracji programu ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Wszystkie elementy w schemacie konfiguracji platformy ASP.NET, które zawierają elementy umożliwiające konfigurację witryn sieci Web platformy ASP.NET i aplikacji. Używane w *Web.config* plików. |
| [ **\<usługi sieci Web >** schemat ustawień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Wszystkie elementy w schemacie ustawień usług sieci Web. |
| [Schemat ustawień internetowych](~/docs/framework/configure-apps/file-schema/web/index.md) | Wszystkie elementy w schemacie ustawień sieci Web zawierają elementy umożliwiające konfigurację działania programu ASP.NET z aplikacją hosta, takich jak usługi IIS. Używane w *aspnet.config* plików. |

## <a name="remarks"></a>Uwagi

Każdy plik konfiguracji musi zawierać dokładnie jeden  **\<konfiguracji >** elementu.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
