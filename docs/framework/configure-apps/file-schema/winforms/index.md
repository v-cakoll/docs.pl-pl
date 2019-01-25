---
title: Sekcja konfiguracji programu Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb2c4157ba702182056c98c959a60569e8c3d1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649481"
---
# <a name="windows-forms-configuration-section"></a>Sekcja konfiguracji programu Windows Forms
Ustawienia konfiguracji formularze Windows umożliwiają aplikacji Windows Forms, do przechowywania i pobierania informacji o aplikacji dostosowane ustawienia, takie jak obsługa wielu monitorów, obsługa wysokiej rozdzielczości DPI i inne wstępnie zdefiniowane ustawienia konfiguracji.

Ustawienia konfiguracji aplikacji Windows Forms są przechowywane w pliku konfiguracyjnym aplikacji `System.Windows.Forms.ApplicationConfigurationSection` elementu.

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
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | Dodaje klucz Ustawienia konfiguracji z określoną wartością |

### <a name="parent-elements"></a>Elementy nadrzędne

Element  |Opis |
---------|---------|
[\<Konfiguracja >](../configuration-element.md) | Element główny w każdym pliku konfiguracji używane przez środowisko uruchomieniowe języka wspólnego i Windows Forms aplikacji |

## <a name="remarks"></a>Uwagi

Począwszy od .NET Framework 4.7 `<System.Windows.Forms.ApplicationConfigurationSection>` elementu umożliwia skonfigurowanie aplikacji Windows Forms, aby wykorzystać funkcje dodane w najnowszych wersjach programu .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Element może zawierać co najmniej jedną podrzędną [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elementów, z których każdy definiuje ustawienia konfiguracji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Obsługa wysokiej rozdzielczości w formularzach Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
