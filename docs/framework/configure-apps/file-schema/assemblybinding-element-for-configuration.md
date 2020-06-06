---
title: <assemblyBinding>, element dla <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155482"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding>, element dla \<configuration>

Określa zasady powiązań zestawów na poziomie konfiguracji.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**

## <a name="syntax"></a>Składnia

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **'xmlns** | Atrybut wymagany.<br><br>Określa przestrzeń nazw XML wymaganą dla powiązania zestawu. Użyj ciągu "urn: schematys-Microsoft-com: ASM. v1" jako wartości. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-element"></a>Element podrzędny

|     | Opis |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | Określa plik konfiguracji, który ma zostać uwzględniony. |

## <a name="remarks"></a>Uwagi

[**\<linkedConfiguration>**](linkedconfiguration-element.md)Element upraszcza zarządzanie zestawami składników przez zezwolenie plikom konfiguracji aplikacji na uwzględnianie plików konfiguracji zestawu w dobrze znanych lokalizacjach, a nie duplikowanie ustawień konfiguracji zestawu.

> [!NOTE]
> **\<linkedConfiguration>** Element nie jest obsługiwany w przypadku aplikacji z manifestami równoległymi systemu Windows.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dołączyć plik konfiguracji na lokalnym dysku twardym:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
