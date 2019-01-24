---
title: Ustawienia aplikacji dotyczące kontrolek niestandardowych
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 96145a6205c3e80b23f3c69750f7faaec04aabba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526746"
---
# <a name="application-settings-for-custom-controls"></a>Ustawienia aplikacji dotyczące kontrolek niestandardowych
Należy wykonać niektóre zadania, aby zapewnić możliwość utrzymania ustawienia aplikacji, gdy kontrolki znajdują się w aplikacji innych firm Kontrolki niestandardowe.  
  
 Większość dokumentacji dotyczącej funkcji ustawienia aplikacji są zapisywane przy założeniu, tworzysz oddzielną aplikację. Jednak jeśli tworzysz formant, który będzie obsługiwał innym deweloperom w swoich aplikacjach, należy wykonać kilka dodatkowych kroków kontrolki do utrwalania jego ustawienia prawidłowo.  
  
## <a name="application-settings-and-custom-controls"></a>Ustawienia aplikacji i kontrolek niestandardowych  
 Kontrolki można utrwalić prawidłowo jego ustawienia, jego hermetyzacji proces, tworząc własne dedykowane aplikacje klasy otoki ustawienia pochodzące z <xref:System.Configuration.ApplicationSettingsBase>. Ponadto musi implementować klasę główną kontrolką <xref:System.Configuration.IPersistComponentSettings>. Interfejs zawiera kilka właściwości, a także dwie metody <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> i <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Jeśli dodasz formant do formularza przy użyciu **Windows Forms Designer** w programie Visual Studio, Windows Forms będzie wywoływać <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatycznie, gdy formant jest inicjowany; należy wywołać <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> samodzielnie w `Dispose` Metoda formantu.  
  
 Ponadto należy zaimplementować następujące czynności w kolejności dla ustawienia aplikacji dotyczące kontrolek niestandardowych działać poprawnie w czasie projektowania środowiskach, takich jak Visual Studio:  
  
1.  Klasa ustawień niestandardowych aplikacji, za pomocą konstruktora przyjmującego <xref:System.ComponentModel.IComponent> jako jeden parametr. Użyj tej klasy, aby zapisać i załadować wszystkie ustawienia aplikacji. Podczas tworzenia nowego wystąpienia tej klasy, należy przekazać niestandardową kontrolkę za pomocą konstruktora.  
  
2.  Tworzenie tej klasy ustawienia niestandardowe, po utworzeniu kontrolki i umieszczane na formularzu, takie jak w postaci <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.  
  
 Aby uzyskać instrukcje na temat tworzenia klasy ustawień niestandardowych, zobacz [jak: Tworzenie ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Ustawienia kluczy i wspólnych ustawień  
 Niektóre formanty mogą być używane wielokrotnie w ramach tego samego formularza. W większości przypadków, należy te kontrolki do utrwalania indywidualne ustawienia. Za pomocą <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> właściwość <xref:System.Configuration.IPersistComponentSettings>, możesz podać unikatowy ciąg, który działa do odróżniania wielu wersji kontrolkę w formularzu.  
  
 Najprostszym sposobem wdrożenia <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> jest użycie <xref:System.Windows.Forms.Control.Name%2A> właściwości formantu dla <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Podczas ładowania lub zapisywania ustawienia kontroli, należy przekazać wartość <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> do <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> właściwość <xref:System.Configuration.ApplicationSettingsBase> klasy. Ustawienia aplikacji używa tego unikatowego klucza, gdy utrzymuje ustawienia użytkownika do pliku XML. Poniższy kod przedstawia przykład sposobu `<userSettings>` sekcja może wyglądać w przypadku wystąpienia kontrolkę niestandardową o nazwie `CustomControl1` który zapisuje ustawienie dla jego `Text` właściwości.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Wszystkie wystąpienia formant, który nie zostanie podana wartość <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> współużytkują te same ustawienia.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Architektura ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
