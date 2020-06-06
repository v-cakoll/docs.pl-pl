---
title: Sekcja konfiguracji programu Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151835"
---
# <a name="windows-forms-configuration-section"></a>Sekcja konfiguracji programu Windows Forms
Windows Forms ustawienia konfiguracji umożliwiają aplikacji Windows Forms przechowywanie i pobieranie informacji o niestandardowych ustawieniach aplikacji, takich jak obsługa wielomonitorów, obsługa wysokiej rozdzielczości DPI i inne wstępnie zdefiniowane ustawienia konfiguracji.

Ustawienia konfiguracji aplikacji Windows Forms są przechowywane w pliku konfiguracji aplikacji `System.Windows.Forms.ApplicationConfigurationSection` .

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
[`<add>`](windows-forms-add-configuration-element.md) | Dodaje klucz ustawienia konfiguracji z określoną wartością |

### <a name="parent-elements"></a>Elementy nadrzędne

Element  |Opis |
---------|---------|
[\<configuration>](../configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje Windows Forms |

## <a name="remarks"></a>Uwagi

Począwszy od .NET Framework 4,7, `<System.Windows.Forms.ApplicationConfigurationSection>` element pozwala konfigurować aplikacje Windows Forms, aby korzystać z funkcji dodanych w ostatnich wersjach .NET Framework.

`<System.Windows.Forms.ApplicationConfigurationSection>`Element może zawierać jeden lub więcej elementów podrzędnych [`<add>`](windows-forms-add-configuration-element.md) , z których każda definiuje określone ustawienie konfiguracji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Obsługa wysokiej rozdzielczości DPI w Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
