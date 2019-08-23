---
title: Renderowanie formantów przy użyciu stylów wizualnych
ms.date: 03/30/2017
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
ms.openlocfilehash: 32bcbab585c39be4a72150bf49820d4a16f1691f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968247"
---
# <a name="rendering-controls-with-visual-styles"></a>Renderowanie formantów przy użyciu stylów wizualnych
.NET Framework zapewnia obsługę formantów renderowania i innych elementów interfejsu użytkownika systemu Windows przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują. W tym temacie omówiono kilka poziomów wsparcia w .NET Framework do renderowania formantów i innych elementów interfejsu użytkownika z obecnym stylem wizualnym systemu operacyjnego.  
  
## <a name="rendering-classes-for-common-controls"></a>Klasy renderowania dla formantów wspólnych  
 Renderowanie kontrolki odwołuje się do rysowania interfejsu użytkownika kontrolki. <xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw <xref:System.Windows.Forms.ControlPaint> udostępnia klasę do renderowania niektórych typowych formantów Windows Forms. Jednak ta klasa rysuje kontrolki w klasycznym stylu systemu Windows, co może utrudnić zachowanie spójnego interfejsu użytkownika podczas rysowania niestandardowych kontrolek w aplikacjach z włączonymi stylami wizualizacji.  
  
 .NET Framework 2,0 zawiera klasy w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw, które renderuje części i Stany wspólnych formantów przy użyciu stylów wizualnych. Każda z tych klas obejmuje `static` metody rysowania kontrolki lub części formantu w określonym stanie z obecnym stylem wizualnym systemu operacyjnego.  
  
 Niektóre z tych klas zostały zaprojektowane do rysowania powiązanej kontroli, niezależnie od tego, czy style wizualne są dostępne. Jeśli style wizualizacji są włączone, członkowie klasy będą rysować powiązane kontrolki ze stylami wizualnymi; Jeśli style wizualizacji są wyłączone, elementy członkowskie klasy będą rysowane w klasycznym stylu systemu Windows. Te klasy obejmują:  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Inne klasy mogą narysować powiązane kontrolki tylko wtedy, gdy style wizualizacji są dostępne, a ich członkowie będą zgłaszać wyjątek, jeśli style wizualizacji są wyłączone. Te klasy obejmują:  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Aby uzyskać więcej informacji na temat używania tych klas do narysowania kontrolki, zobacz [How to: Użyj klasy](how-to-use-a-control-rendering-class.md)renderowania formantów.  
  
## <a name="visual-style-element-and-rendering-classes"></a>Element stylu wizualizacji i klasy renderowania  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy, których można użyć do rysowania i uzyskiwania informacji o dowolnym formancie lub elemencie interfejsu użytkownika, który jest obsługiwany przez style wizualne. Obsługiwane formanty obejmują typowe kontrolki, które mają klasę renderingu <xref:System.Windows.Forms?displayProperty=nameWithType> w przestrzeni nazw (zobacz poprzednią sekcję), a także inne kontrolki, takie jak kontrolki karty i kontrolki paska pomocniczego. Inne obsługiwane elementy interfejsu użytkownika obejmują części menu **Start** , paska zadań i nieklienckiego obszaru systemu Windows.  
  
 Główne klasy <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeni nazw to <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> i <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>jest klasą fundamentową do identyfikowania dowolnego elementu formantu lub interfejsu użytkownika obsługiwanego przez style wizualne. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> Oprócz siebie <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> , przestrzeń nazw zawiera wiele zagnieżdżonych klas z `static` właściwościami, które zwracają dla każdego stanu kontrolki, części formantu lub innego elementu interfejsu użytkownika obsługiwanego przez wizualizację <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Style.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>udostępnia metody, które rysują i pobierają informacje <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> o każdej z nich zdefiniowanej przez bieżący styl wizualny systemu operacyjnego. Informacje, które można pobrać dla elementu, obejmują jego domyślny rozmiar, typ tła i definicje kolorów. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>Zawija funkcję interfejsu API stylów wizualnych (UxTheme) z części powłoki systemu Windows zestawu SDK platformy systemu Windows. Aby uzyskać więcej informacji, zobacz [Włączanie stylów wizualnych](/windows/desktop/controls/cookbook-overview).  
  
 Aby uzyskać więcej informacji na <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> temat <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>korzystania z [i, zobacz How to: Renderowanie elementu](how-to-render-a-visual-style-element.md)stylu wizualnego.  
  
## <a name="enabling-visual-styles"></a>Włączanie stylów wizualnych  
 Aby włączyć style wizualne dla aplikacji zapisaną dla .NET Framework wersji 1,0, programiści muszą zawierać manifest aplikacji, który określa, że ComCtl32. dll w wersji 6 lub nowszej zostanie użyta do rysowania kontrolek. Aplikacje skompilowane przy użyciu .NET Framework w wersji 1,1 lub nowszej mogą <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> korzystać z metody <xref:System.Windows.Forms.Application> klasy.  
  
## <a name="checking-for-visual-styles-support"></a>Sprawdzanie obsługi stylów wizualnych  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Właściwość<xref:System.Windows.Forms.Application> klasy wskazuje, czy bieżąca aplikacja rysuje kontrolki przy użyciu stylów wizualnych. Podczas malowania kontrolki niestandardowej można sprawdzić wartość <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> , aby określić, czy formant ma być renderowany z lub bez stylów wizualnych. W poniższej tabeli wymieniono cztery warunki, które muszą istnieć <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> , aby `true`można było zwrócić.  
  
|Warunek|Uwagi|  
|---------------|-----------|  
|System operacyjny obsługuje style wizualne.|Aby sprawdzić ten warunek oddzielnie, użyj <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> właściwości <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> klasy.|  
|Użytkownik włączył style wizualne w systemie operacyjnym.|Aby sprawdzić ten warunek oddzielnie, użyj <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> właściwości <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> klasy.|  
|Style wizualizacji są włączone w aplikacji.|Style wizualne można włączyć w aplikacji przez wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody lub przy użyciu manifestu aplikacji, który określa, że comctl32. dll w wersji 6 lub nowszej zostanie użyta do rysowania kontrolek.|  
|Style wizualizacji są używane do rysowania obszaru klienta w oknach aplikacji.|Aby sprawdzić ten warunek oddzielnie, <xref:System.Windows.Forms.Application.VisualStyleState%2A> Użyj właściwości <xref:System.Windows.Forms.Application> klasy i sprawdź, czy ma ona wartość <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> lub <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Aby określić, kiedy użytkownik włącza lub wyłącza style wizualizacji, lub przełącza z jednego stylu wizualizacji na inny, należy <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> sprawdzić wartość w obszarze obsługi <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> dla zdarzeń lub <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
> Jeśli chcesz użyć <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> do renderowania kontrolki lub elementu interfejsu użytkownika, gdy użytkownik włącza lub przełącza style wizualne, należy się upewnić, że jest to konieczne podczas <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> obsługi zdarzenia zamiast <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> zdarzenia. Wyjątek zostanie wygenerowany, <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> Jeśli użyjesz klasy podczas obsługi. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>  
  
## <a name="see-also"></a>Zobacz także

- [Malowanie i renderowanie kontrolki niestandardowej](custom-control-painting-and-rendering.md)
