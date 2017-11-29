---
title: "Ustawienia aplikacji dotyczące kontrolek niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f8292ac459a2943376229ef62466b0a772430dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-for-custom-controls"></a>Ustawienia aplikacji dotyczące kontrolek niestandardowych
Należy wykonać pewne zadania, aby zapewnić możliwość utrzymania ustawienia aplikacji, jeśli formanty są hostowane w aplikacjach innych firm Kontrolki niestandardowe.  
  
 Większość dokumentacji dotyczące funkcji ustawienia aplikacji jest zapisywany przy założeniu, że tworzona aplikacja autonomiczna. Jednak w przypadku tworzenia formant, który będzie hostem inni deweloperzy w aplikacjach, należy wykonać kilka dodatkowych kroków formantu do utrwalenia jego ustawienia poprawnie.  
  
## <a name="application-settings-and-custom-controls"></a>Ustawienia aplikacji i kontrolek niestandardowych  
 Dla formantu prawidłowo utrwalić jego ustawienia, go Hermetyzowanie procesu przez utworzenie własnego dedykowanego aplikacjami klasy otoki ustawień, pochodzących z <xref:System.Configuration.ApplicationSettingsBase>. Ponadto należy zaimplementować klasy głównym formantu <xref:System.Configuration.IPersistComponentSettings>. Interfejs zawiera wiele właściwości, jak również dwie metody <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> i <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Po dodaniu formantu do formularza używającego **Projektant formularzy systemu Windows** w programie Visual Studio, formularze systemu Windows będzie wywoływać <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatycznie, gdy formant jest inicjowany; należy wywołać <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> samodzielnie w `Dispose` Metoda formantu.  
  
 Ponadto należy zaimplementować następujące w kolejności dla ustawienia aplikacji w przypadku kontrolek niestandardowych do poprawnego działania w czasie projektowania środowisk takiego jak Visual Studio:  
  
1.  Klasa ustawień niestandardowych aplikacji z konstruktora przyjmującego <xref:System.ComponentModel.IComponent> jako jeden parametr. Ta klasa umożliwia zapisywanie i ładowanie wszystkie ustawienia aplikacji. Podczas tworzenia nowego wystąpienia tej klasy należy przekazać formantu niestandardowego za pomocą konstruktora.  
  
2.  Tworzenie tej klasy niestandardowe ustawienia po utworzeniu i umieszczane na formularzu, takie jak w postaci formantu <xref:System.Windows.Forms.Form.Load> obsługi zdarzeń.  
  
 Aby uzyskać instrukcje tworzenia klasy ustawień niestandardowych, zobacz [porady: Tworzenie ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Ustawienia kluczy i ustawienia udostępnione  
 Niektóre formanty mogą być używane wielokrotnie w ramach tego samego formularza. W większości przypadków, można tych kontrolek można utrwalić własne poszczególnych ustawień. Z <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> właściwość <xref:System.Configuration.IPersistComponentSettings>, możesz podać unikatowy ciąg, który służy do odróżniania wielu wersji kontrolkę w formularzu.  
  
 Najprostszym sposobem, aby zaimplementować <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> jest użycie <xref:System.Windows.Forms.Control.Name%2A> właściwości formantu <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Po załadowaniu lub Zapisz ustawienia kontroli przekazać wartość <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> do <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> właściwość <xref:System.Configuration.ApplicationSettingsBase> klasy. Ustawienia aplikacji używa to unikatowy klucz, jeśli będzie się powtarzał ustawienia użytkownika do pliku XML. Poniższy kod przedstawia przykład sposobu `<userSettings>` sekcji może wyszukać wystąpienia niestandardowego formantu o nazwie `CustomControl1` który zapisuje ustawienie dla jego `Text` właściwości.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Wszystkie wystąpienia formantu, który nie zostanie podana wartość <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> będzie mają te same ustawienia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Architektura ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
