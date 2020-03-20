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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155482"
---
# <a name="assemblybinding-element-for-configuration"></a>\<element> \<do konfiguracji>

Określa zasady wiązania zestawu na poziomie konfiguracji.

konfiguracja &nbsp; &nbsp;>[** \<**](configuration-element.md) ** \<montażUUwiązanie>**

## <a name="syntax"></a>Składnia

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Xmlns** | Atrybut wymagany.<br><br>Określa obszar nazw XML wymagany dla powiązania zestawu. Użyj ciągu "urn:schemas-microsoft-com:asm.v1" jako wartości. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<>konfiguracyjne**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-element"></a>Element podrzędny

|     | Opis |
| --- | ----------- |
| [**\<>konfiguracji linkedConfiguration**](linkedconfiguration-element.md) | Określa plik konfiguracji do uwzględnienia. |

## <a name="remarks"></a>Uwagi

Element [** \<>linkedConfiguration**](linkedconfiguration-element.md) upraszcza zarządzanie zestawami komponentów, umożliwiając plikom konfiguracyjnym aplikacji dołączanie plików konfiguracyjnych w dobrze znanych lokalizacjach, a nie duplikowanie ustawień konfiguracji zestawu.

> [!NOTE]
> Element ** \<linkedConfiguration>** nie jest obsługiwany dla aplikacji z manifestami obok siebie systemu Windows.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak dołączyć plik konfiguracyjny na lokalnym dysku twardym:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracyjnego programu .NET Framework](index.md)
