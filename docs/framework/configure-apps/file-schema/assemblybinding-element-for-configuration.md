---
title: <assemblyBinding>, element dla <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921273"
---
# <a name="assemblybinding-element-for-configuration"></a>\<zestawbinding > elementu \<> konfiguracji

Określa zasady powiązań zestawów na poziomie konfiguracji.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp; **\<> zestawubinding**

## <a name="syntax"></a>Składnia

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **xmlns** | Atrybut wymagany.<br><br>Określa przestrzeń nazw XML wymaganą dla powiązania zestawu. Użyj ciągu "urn: schematys-Microsoft-com: ASM. v1" jako wartości. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<> konfiguracji**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-element"></a>Element podrzędny

|     | Opis |
| --- | ----------- |
| [ **\<linkedConfiguration>** ](linkedconfiguration-element.md) | Określa plik konfiguracji, który ma zostać uwzględniony. |

## <a name="remarks"></a>Uwagi

[ **\<Linkedconfiguration — >** ](linkedconfiguration-element.md) element ułatwia zarządzanie zestawów składników, umożliwiając pliki konfiguracji aplikacji do dołączenia zestawu plików konfiguracji w lokalizacje znane zamiast duplikowania ustawienia konfiguracji zestawu.

> [!NOTE]
> **\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.

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
