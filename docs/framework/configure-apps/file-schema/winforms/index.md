---
title: Sekcja konfiguracji programu Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151835"
---
# <a name="windows-forms-configuration-section"></a>Sekcja konfiguracji programu Windows Forms
Ustawienia konfiguracji Formularzy systemu Windows umożliwiają aplikacji Windows Forms przechowywanie i pobieranie informacji o dostosowanych ustawieniach aplikacji, takich jak obsługa wielu monitorów, obsługa wysokiej rozdzielczości DPI i inne wstępnie zdefiniowane ustawienia konfiguracji.

Ustawienia konfiguracji aplikacji Windows Forms są przechowywane `System.Windows.Forms.ApplicationConfigurationSection` w elemencie pliku konfiguracji aplikacji.

## <a name="syntax"></a>Składnia

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Element  |Opis |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | Dodaje klucz ustawień konfiguracji o określonej wartości |

### <a name="parent-elements"></a>Elementy nadrzędne

Element  |Opis |
---------|---------|
[\<>konfiguracyjne](../configuration-element.md) | Element główny w każdym pliku konfiguracyjnym używanym przez środowisko wykonawcze języka wspólnego i aplikacje Windows Forms |

## <a name="remarks"></a>Uwagi

Począwszy od programu .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element umożliwia skonfigurowanie aplikacji Windows Forms, aby korzystać z funkcji dodanych w ostatnich wersjach programu .NET Framework.

Element `<System.Windows.Forms.ApplicationConfigurationSection>` może zawierać jeden [`<add>`](windows-forms-add-configuration-element.md) lub więcej elementów podrzędnych, z których każdy definiuje określone ustawienie konfiguracji.

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracji](../index.md)
- [Obsługa wysokiej rozdzielczości DPI w formularzach systemu Windows](../../../winforms/high-dpi-support-in-windows-forms.md)
