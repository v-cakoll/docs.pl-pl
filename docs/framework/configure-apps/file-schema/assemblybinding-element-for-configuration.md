---
title: "&lt;assemblybinding —&gt; elementu &lt;konfiguracji&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 8d670c56a885a5fdae059a87f63fba9ab32f020c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblybinding — > elementu \<configuration >

Określa zestaw powiązania zasad na poziomie konfiguracji.

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
| **xmlns** | Atrybut wymagany.<br><br>Określa przestrzeń nazw XML, wymagane do powiązań zestawów. Należy użyć ciągu "urn: schemas-microsoft-com:asm.v1" jako wartości. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-element"></a>Element podrzędny

|     | Opis |
| --- | ----------- |
| [**\<linkedconfiguration — >**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | Określa plik konfiguracji do uwzględnienia. |

## <a name="remarks"></a>Uwagi

[  **\<Linkedconfiguration — >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element upraszcza zarządzanie zestawów składników, zezwalając pliki konfiguracji aplikacji, aby uwzględnić zestawu plików konfiguracyjnych w dobrze znanej lokalizacji, a nie ustawienia konfiguracji usługi zduplikować zestawu.

> [!NOTE]
>  **\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o manifestów side-by-side systemu Windows.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dołączenie pliku konfiguracji na lokalnym dysku twardym:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
