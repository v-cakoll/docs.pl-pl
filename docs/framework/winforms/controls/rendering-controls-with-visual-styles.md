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
ms.openlocfilehash: a7f2d810567d37021d5d4473204d9950d6834b9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540907"
---
# <a name="rendering-controls-with-visual-styles"></a>Renderowanie formantów przy użyciu stylów wizualnych
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia obsługę renderowania kontrolek i innych użytkowników systemu Windows elementy interfejsu użytkownika przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują. W tym temacie omówiono kilka poziomów obsługi w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dla formantów renderowania i inne elementy interfejsu użytkownika z aktualnym stylu wizualnym systemu operacyjnego.  
  
## <a name="rendering-classes-for-common-controls"></a>Klasy renderowania dla formantów standardowych  
 Renderowanie formantu odwołuje się do rysowania formantu interfejsu użytkownika. <xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw zawiera <xref:System.Windows.Forms.ControlPaint> klasy renderowania niektóre typowe formanty formularzy systemu Windows. Jednak ta klasa rysuje formantów w klasycznym stylu systemu Windows, który może utrudniać Obsługa spójne środowisko interfejsu użytkownika po włączeniu rysowania niestandardowych formantów w aplikacji przy użyciu stylów wizualnych.  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] Zawiera klasy w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw, renderowanie części i stanów wspólnych formantów przy użyciu stylów wizualnych. Każda z tych klas zawiera `static` metody służące do rysowania formant lub części formantu w określonym stanie z aktualnym stylu wizualnym systemu operacyjnego.  
  
 Niektóre z tych klas są przeznaczone do rysowania pokrewnej kontrolki niezależnie od tego, czy style wizualne są dostępne. Jeżeli style wizualne są włączone, następnie elementów członkowskich klasy narysuje pokrewnej kontrolki przy użyciu stylów wizualnych; Jeżeli style wizualne są wyłączone, elementy członkowskie klasy będzie narysować kontrolkę w stylu klasycznym systemu Windows. Klasy te obejmują:  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Inne klasy tylko narysować pokrewnej kontrolki podczas style wizualne są dostępne, i ich elementy członkowskie spowoduje zgłoszenie wyjątku, jeżeli style wizualne są wyłączone. Klasy te obejmują:  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Aby uzyskać więcej informacji na temat używania tych klas do rysowania formantu zobacz [porady: używanie klasy renderowania formantu](../../../../docs/framework/winforms/controls/how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Element stylu wizualnego i renderowania klas  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy, które mogą służyć do rysowania i uzyskać informacje na temat kontroli ani elementu interfejsu użytkownika, który jest obsługiwany przez stylów wizualnych. Są obsługiwane kontrolki typowych formantów, które mają klasy renderowania w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw (zobacz poprzedniej sekcji), a także inne formanty, takie jak formanty karty i formanty paska pomocniczego. Inne obsługiwane elementy interfejsu użytkownika obejmują części **Start** menu, paska zadań i obszar niekliencki systemu windows.  
  
 Klasy głównym <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeni nazw są <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> i <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> jest klasą foundation identyfikacji dowolnego elementu interfejsu formant lub użytkownika, obsługiwane przez stylów wizualnych. Oprócz <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> , <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeń nazw zawiera wiele zagnieżdżonych klas <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> z `static` właściwości, które zwracają <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> dla każdego stanu formantu, część kontroli lub innego elementu interfejsu użytkownika obsługiwanych przez visual style.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> udostępnia metody, które rysowania i uzyskać informacje o poszczególnych <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> wynika z aktualnym stylu wizualnym systemu operacyjnego. Gdy można pobrać informacje o elemencie obejmuje jego domyślny rozmiar, typ tła i definicje kolorów. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> opakowuje funkcję style wizualne (UxTheme) interfejsu API z powłoki Windows części zestawu SDK platformy Windows. Aby uzyskać więcej informacji, zobacz [przy użyciu style wizualne XP Windows](https://msdn.microsoft.com/library/ms997649.aspx).  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> i <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, zobacz [porady: renderowanie elementu stylu wizualnego](../../../../docs/framework/winforms/controls/how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Włączanie style wizualne  
 Aby włączyć style wizualne dla aplikacji napisanych dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.0 programistów musi zawierać manifest aplikacji, która określa, że ComCtl32.dll w wersji 6 lub nowszej będzie używany do rysowania formantów. Aplikacji skompilowanej za pomocą [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 lub nowszej można użyć <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.Application> klasy.  
  
## <a name="checking-for-visual-styles-support"></a>Sprawdzanie, czy Obsługa stylów wizualnych  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Właściwość <xref:System.Windows.Forms.Application> klasy wskazuje, czy bieżąca aplikacja jest rysowania formantów przy użyciu stylów wizualnych. Malowanie kontrolki niestandardowej, należy sprawdzić wartość <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> ustalenie, czy mają renderować formantu z lub bez stylów wizualnych. W poniższej tabeli przedstawiono cztery warunki, które musi istnieć dla <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> do zwrócenia `true`.  
  
|Warunek|Uwagi|  
|---------------|-----------|  
|System operacyjny obsługuje stylów wizualnych.|Aby sprawdzić oddzielnie ten warunek, użyj <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> właściwość <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> klasy.|  
|Użytkownik ma włączyć style wizualne w systemie operacyjnym.|Aby sprawdzić oddzielnie ten warunek, użyj <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> właściwość <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> klasy.|  
|Style wizualne są włączone w aplikacji.|Style wizualne można włączyć w aplikacji przez wywołanie metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody lub za pomocą aplikacji do manifestu, który określa, że wersja pliku ComCtl32.dll 6 lub nowszej będzie używany do rysowania formantów.|  
|Style wizualne są używane do rysowania obszaru klienckiego aplikacji systemu windows.|Aby sprawdzić oddzielnie ten warunek, użyj <xref:System.Windows.Forms.Application.VisualStyleState%2A> właściwość <xref:System.Windows.Forms.Application> klasy i sprawdź, czy wartość <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> lub <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Aby ustalić, kiedy użytkownik umożliwia wyłącza style wizualne lub zmienia się z jednego stylu wizualnego do innego, wyszukaj <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> wartość programy obsługi <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> lub <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> zdarzenia.  
  
> [!IMPORTANT]
>  Jeśli chcesz użyć <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> do renderowania formantu lub elementu interfejsu użytkownika, gdy użytkownik włączy lub zmienia stylów wizualnych, upewnij się, to zrobić podczas obsługi <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń zamiast <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> zdarzeń. Jeśli używasz będzie zgłaszany wyjątek <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> klasy podczas obsługi <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Zobacz też  
 [Malowanie i renderowanie kontrolki niestandardowej](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)
