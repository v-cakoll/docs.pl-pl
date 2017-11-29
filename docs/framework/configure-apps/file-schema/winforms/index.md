---
title: Sekcja konfiguracji formularzy systemu Windows
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b83f00f82de727812c5737915a6dc35ec98e4734
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-configuration-section"></a>Sekcja konfiguracji formularzy systemu Windows
Ustawienia konfiguracji formularzy systemu Windows umożliwiają aplikacji formularzy systemu Windows, do przechowywania i pobierania informacji o aplikacji dostosowane ustawienia, takie jak obsługi wielu monitorów, wysokiej rozdzielczości DPI pomocy technicznej i inne wstępnie zdefiniowane ustawienia konfiguracji.

Ustawienia konfiguracji aplikacji formularzy systemu Windows są przechowywane w pliku konfiguracyjnym aplikacji `System.Windows.Forms.ApplicationConfigurationSection` elementu.

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
[\<Konfiguracja >](../configuration-element.md) | Element główny w każdym pliku konfiguracyjnym używane przez środowisko uruchomieniowe języka wspólnego i formularze systemu Windows, aplikacje |

## <a name="remarks"></a>Uwagi

W programie .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element pozwala na skonfigurowanie aplikacji formularzy systemu Windows, aby wykorzystać funkcje dodane w najnowszych wersjach programu .NET Framework. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Elementu mogą zawierać jeden lub więcej podrzędnych [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elementów, z których każdy definiuje ustawienie określonej konfiguracji.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji](../index.md)   
[Obsługa wysokiej rozdzielczości w formularzach systemu Windows](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
