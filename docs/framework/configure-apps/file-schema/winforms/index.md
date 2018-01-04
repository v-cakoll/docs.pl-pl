---
title: Sekcja konfiguracji programu Windows Forms
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
ms.workload: dotnet
ms.openlocfilehash: f2d83f5dcf6fa93ceba4d670470bd768a2ee1f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-configuration-section"></a>Sekcja konfiguracji programu Windows Forms
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
