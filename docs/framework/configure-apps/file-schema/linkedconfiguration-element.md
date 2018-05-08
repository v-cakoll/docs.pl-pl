---
title: '&lt;linkedconfiguration —&gt; — element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 71769efa1233fc8a693219dc02ae56ea39c164e7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="linkedconfiguration-element"></a>\<linkedconfiguration — > — element

Określa plik konfiguracji do uwzględnienia.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblybinding — >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedconfiguration — >**

## <a name="syntax"></a>Składnia

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **href**  | Atrybut wymagany.<br><br>Adres URL pliku konfiguracji, aby uwzględnić. Jedynym obsługiwanym formatem do **href** atrybutu `file://`. Lokalnych plików i plików UNC są obsługiwane. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<assemblybinding — >** — Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Określa zestaw powiązania zasad na poziomie konfiguracji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<Linkedconfiguration — >** element upraszcza obsługi dla zestawów składników. Użycie zestawu, który zawiera plik konfiguracji znajdujących się w dobrze znanej lokalizacji, co najmniej jednej aplikacji można użyć pliki konfiguracji aplikacji, które używają zestawu  **\<linkedconfiguration — >** element do uwzględnienia w pliku konfiguracji zestawu, a nie bezpośrednio w tym informacje o konfiguracji. Gdy zestaw składników jest obsługiwana, aktualizowania typowych plik konfiguracji zawiera informacje zaktualizowanej konfiguracji we wszystkich aplikacjach korzystających z zestawu.

> [!NOTE]
> **\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o manifestów side-by-side systemu Windows.

Następujące reguły kontrolować używanie powiązane pliki konfiguracji:

- Ustawień w plikach konfiguracji dołączone tylko wpływa na zasady powiązanie modułu ładującego i są używane tylko przez moduł ładujący. Pliki konfiguracji dołączone może mieć ustawienia inne niż powiązanie zasady, ale te ustawienia nie ma żadnego efektu.

- Jedynym obsługiwanym formatem do `href` atrybutu `file://`. Lokalnych plików i plików UNC są obsługiwane.

- Brak ograniczeń dotyczących liczba połączonych konfiguracji dla każdego pliku konfiguracji nie istnieje.

- Wszystkie powiązane pliki konfiguracji zostaną scalone tworzą jeden plik podobne do zachowania `#include` dyrektywy języka C/C++.

- **\<Linkedconfiguration — >** element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowana w *Machine.config*.

- Odwołania cykliczne są wykrywane i zakończone. Oznacza to, że jeśli  **\<linkedconfiguration — >** elementy z szeregu plików konfiguracyjnych tworzą pętlę, pętli są wykrywane i zatrzymać.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób pliku konfiguracji z lokalnego dysku twardego obejmują:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Zobacz także

[**\<assemblybinding — >** — Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
