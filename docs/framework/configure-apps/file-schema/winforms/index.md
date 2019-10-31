---
title: Sekcja konfiguracji programu Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4a54df0b6301f1aae14d5561c91c6792cb0a1620
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109814"
---
# <a name="windows-forms-configuration-section"></a>Sekcja konfiguracji programu Windows Forms
Windows Forms ustawienia konfiguracji umożliwiają aplikacji Windows Forms przechowywanie i pobieranie informacji o niestandardowych ustawieniach aplikacji, takich jak obsługa wielomonitorów, obsługa wysokiej rozdzielczości DPI i inne wstępnie zdefiniowane ustawienia konfiguracji.

Ustawienia konfiguracji aplikacji Windows Forms są przechowywane w elemencie `System.Windows.Forms.ApplicationConfigurationSection` pliku konfiguracji aplikacji.

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
[> konfiguracji \<](../configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje Windows Forms |

## <a name="remarks"></a>Uwagi

Począwszy od .NET Framework 4,7, element `<System.Windows.Forms.ApplicationConfigurationSection>` umożliwia skonfigurowanie aplikacji Windows Forms, aby korzystać z funkcji dodanych w ostatnich wersjach .NET Framework. 

Element `<System.Windows.Forms.ApplicationConfigurationSection>` może zawierać jeden lub więcej elementów podrzędnych [`<add>`](windows-forms-add-configuration-element.md) , z których każdy definiuje określone ustawienie konfiguracji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Obsługa wysokiej rozdzielczości DPI w Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
