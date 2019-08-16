---
title: Ustawienia aplikacji dotyczące kontrolek niestandardowych
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040459"
---
# <a name="application-settings-for-custom-controls"></a>Ustawienia aplikacji dotyczące kontrolek niestandardowych
Należy wykonać pewne zadania, aby zapewnić, że formanty niestandardowe mogą utrwalać ustawienia aplikacji, gdy formanty są hostowane w aplikacjach innych firm.

 Większość dokumentacji dotyczącej funkcji ustawień aplikacji jest zapisywana w założeniu, że tworzysz aplikację autonomiczną. Jeśli jednak tworzysz kontrolkę, którą inni deweloperzy będą hostować w swoich aplikacjach, musisz wykonać kilka dodatkowych kroków, aby formant prawidłowo utrwalał ustawienia.

## <a name="application-settings-and-custom-controls"></a>Ustawienia aplikacji i kontrolki niestandardowe
 Aby formant prawidłowo utrzymywał swoje ustawienia, musi on hermetyzować proces, tworząc własne klasy otoki ustawień dedykowanych aplikacji pochodne od <xref:System.Configuration.ApplicationSettingsBase>. Ponadto Klasa głównej kontroli musi implementować <xref:System.Configuration.IPersistComponentSettings>. Interfejs zawiera kilka właściwości, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> a także dwie metody i. <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> Jeśli dodasz kontrolkę do formularza przy użyciu **Projektant formularzy systemu Windows** w programie Visual Studio, Windows Forms zostanie wywołana <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatycznie po zainicjowaniu kontrolki; musisz `Dispose` wywołać <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> siebie w metodzie formantu.

 Ponadto należy zaimplementować następujące elementy, aby ustawienia aplikacji dla formantów niestandardowych działały prawidłowo w środowiskach czasu projektowania, takich jak Visual Studio:

1. Niestandardowa Klasa ustawień aplikacji z konstruktorem, który <xref:System.ComponentModel.IComponent> przyjmuje jako jeden parametr. Ta klasa służy do zapisywania i ładowania wszystkich ustawień aplikacji. Gdy tworzysz nowe wystąpienie tej klasy, Przekaż kontrolkę niestandardową przy użyciu konstruktora.

2. Utwórz tę klasę ustawień niestandardowych po utworzeniu kontrolki i umieszczeniu jej w formularzu, na przykład w programie obsługi <xref:System.Windows.Forms.Form.Load> zdarzeń formularza.

 Instrukcje dotyczące tworzenia klasy ustawień niestandardowych można znaleźć w temacie [How to: Utwórz ustawienia](how-to-create-application-settings.md)aplikacji.

## <a name="settings-keys-and-shared-settings"></a>Klucze ustawień i ustawienia udostępnione
 Niektóre kontrolki mogą być używane wiele razy w tym samym formularzu. W większości przypadków te kontrolki powinny zachować własne ustawienia. Mając właściwość na <xref:System.Configuration.IPersistComponentSettings>, można podać unikatowy ciąg, który działa w celu odróżnienia wielu wersji formantu w formularzu. <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>

 Najprostszym sposobem implementacji <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> jest <xref:System.Windows.Forms.Control.Name%2A> użycie właściwości kontrolki dla elementu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Podczas ładowania lub zapisywania ustawień kontrolki, należy przekazać wartość <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> on <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> do właściwości <xref:System.Configuration.ApplicationSettingsBase> klasy. Ustawienia aplikacji używają tego klucza unikatowego, gdy zachowuje ustawienia użytkownika w formacie XML. Poniższy przykład kodu pokazuje, jak `<userSettings>` sekcja może szukać wystąpienia kontrolki niestandardowej o nazwie `CustomControl1` , która zapisuje ustawienie dla jego `Text` właściwości.

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 Wszystkie wystąpienia kontrolki, które nie dostarczają wartości <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> , będą współużytkować te same ustawienia.

## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Architektura ustawień aplikacji](application-settings-architecture.md)
