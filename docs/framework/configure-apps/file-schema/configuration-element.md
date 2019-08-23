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
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921249"
---
# <a name="configuration-element"></a>\<> elementu konfiguracji

Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.

**\<> konfiguracji**

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
| [ **\<> zestawubinding**](assemblybinding-element-for-configuration.md) | Określa zasady powiązań zestawów na poziomie konfiguracji.|
| [Schemat ustawień > uruchamiania  **\<** ](./startup/index.md) | Wszystkie elementy w schemacie ustawienia uruchamiania. |
| [Schemat ustawień **> środowiska uruchomieniowego \<** ](./runtime/index.md) | Wszystkie elementy w schemacie ustawień środowiska uruchomieniowego. |
| [Schemat ustawień **> System. Runtime. Komunikacja zdalna \<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Wszystkie elementy w schemacie ustawień usług zdalnych. |
| [Schemat ustawień **systemu .net > \<** ](./network/index.md) | Wszystkie elementy w schemacie ustawień sieciowych. |
| [Schemat ustawień > cryptographySettings  **\<** ](./cryptography/index.md) | Wszystkie elementy w schemacie ustawień kryptograficznych. |
| [Schemat sekcji konfiguracji >  **\<** ](configuration-sections-schema.md) | Wszystkie elementy w schemacie ustawień sekcji konfiguracji. |
| [Schemat ustawień śledzenia i debugowania](./trace-debug/index.md) | Wszystkie elementy w schemacie ustawienia śledzenia i debugowania. |
| [Schemat ustawień konfiguracji ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | Wszystkie elementy w schemacie konfiguracji ASP.NET, w tym elementy służące do konfigurowania witryn i aplikacji sieci Web ASP.NET. Używany w plikach *Web. config* . |
| [Schemat ustawień > usług WebServices  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Wszystkie elementy w schemacie ustawień usług sieci Web. |
| [Schemat ustawień internetowych](./web/index.md) | Wszystkie elementy w schemacie ustawień sieci Web, w tym elementy służące do konfigurowania sposobu działania programu ASP.NET z aplikacją hosta, taką jak usługi IIS. Używany w plikach *ASPNET. config* . |

## <a name="remarks"></a>Uwagi

Każdy plik konfiguracyjny musi zawierać dokładnie jeden  **\<element konfiguracji >** .

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
