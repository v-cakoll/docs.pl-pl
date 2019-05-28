---
title: <linkedConfiguration>, element
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
ms.openlocfilehash: 909ee7cbb7cd31cf213f305b23237cb69e295882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674652"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration> element

Określa wymagający uwzględnienia plik konfiguracji.

[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<assemblybinding — >** ](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**

## <a name="syntax"></a>Składnia

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **href**  | Atrybut wymagany.<br><br>Adres URL pliku konfiguracji, aby uwzględnić. Jedynym obsługiwanym formatem do **href** atrybut jest `file://`. Obsługiwane są pliki lokalne i plików UNC. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<assemblybinding — >** — Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Określa politykę powiązania zestawu na poziomie konfiguracji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<Linkedconfiguration — >** element upraszcza obsługę techniczną dla zestawów składników. Co najmniej jednej aplikacji, użycie zestawu, który zawiera plik konfiguracji znajdujących się w lokalizacji, dobrze znanego, pliki konfiguracji aplikacji, które używają zestawu można użyć **\<linkedconfiguration — >** element, aby uwzględnić plik konfiguracji zestawu, a nie bezpośrednio w tym informacje o konfiguracji. Gdy zestaw składników jest obsługiwany, aktualizowanie wspólnego pliku konfiguracji informacje zaktualizowanej konfiguracji do wszystkich aplikacji korzystających z zestawu.

> [!NOTE]
> **\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.

Użycie powiązane pliki konfiguracji decydują następujące reguły:

- Ustawienia w plikach konfiguracyjnych uwzględnione tylko wpływa na zasady tworzenia powiązań modułu ładującego i są używane tylko przez moduł ładujący. Pliki dołączone konfiguracji może mieć ustawienia inne niż powiązanie zasad, ale te ustawienia nie mają żadnego efektu.

- Jedynym obsługiwanym formatem do `href` atrybut jest `file://`. Obsługiwane są pliki lokalne i plików UNC.

- Brak bez ograniczenia na liczbę połączonych konfiguracji każdego pliku konfiguracji.

- Wszystkie powiązane pliki konfiguracji są scalane w celu utworzenia jeden plik, podobne do zachowania `#include` dyrektywy języka C/C++.

- **\<Linkedconfiguration — >** element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowana w *Machine.config*.

- Odwołania cykliczne są wykrywane i zakończone. Oznacza to jeśli **\<linkedconfiguration — >** elementy szeregu plików konfiguracyjnych tworzą pętli, pętla jest wykrywany i zatrzymane.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dołączyć plik konfiguracji z lokalnego dysku twardego:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [ **\<assemblybinding — >** — Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)
- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
