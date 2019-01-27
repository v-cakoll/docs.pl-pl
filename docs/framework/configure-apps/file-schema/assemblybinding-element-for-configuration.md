---
title: '&lt;assemblyBinding&gt; elementu &lt;konfiguracji&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 12065d8bc484f7bbf77ae18c67df1de0845167b2
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083902"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblybinding — >, element dla \<konfiguracji >

Określa politykę powiązania zestawu na poziomie konfiguracji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<assemblybinding — >**

## <a name="syntax"></a>Składnia

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **xmlns** | Atrybut wymagany.<br><br>Określa przestrzeń nazw XML wymagane w celu tworzenia powiązań zestawów. Użyj ciągu "urn: schemas-microsoft-com:asm.v1" jako wartości. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-element"></a>Element podrzędny

|     | Opis |
| --- | ----------- |
| [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | Określa wymagający uwzględnienia plik konfiguracji. |

## <a name="remarks"></a>Uwagi

[  **\<Linkedconfiguration — >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element ułatwia zarządzanie zestawów składników, umożliwiając pliki konfiguracji aplikacji do dołączenia zestawu plików konfiguracji w lokalizacje znane zamiast duplikowania ustawienia konfiguracji zestawu.

> [!NOTE]
>  **\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.

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

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
