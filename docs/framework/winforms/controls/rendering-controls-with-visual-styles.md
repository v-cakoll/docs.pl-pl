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
ms.openlocfilehash: 4dbccfc881e777309394aed9711a93b8a25315be
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592609"
---
# <a name="rendering-controls-with-visual-styles"></a>Renderowanie formantów przy użyciu stylów wizualnych
.NET Framework zapewnia obsługę renderowania kontrolek i innych użytkowników Windows elementów interfejsu (UI), przy użyciu stylów wizualnych w systemach operacyjnych, które je obsługują. W tym temacie omówiono kilka poziomów pomocy technicznej w programie .NET Framework dla formantów renderowania i inne elementy interfejsu użytkownika przy użyciu bieżącego stylu wizualnego systemu operacyjnego.  
  
## <a name="rendering-classes-for-common-controls"></a>Klasy renderowania dla formantów standardowych  
 Renderowanie formantu odwołuje się do rysowania kontrolki interfejsu użytkownika. <xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw zawiera <xref:System.Windows.Forms.ControlPaint> kontrolek formularzy Windows klasy renderowania niektórych typowych. Jednak ta klasa rysuje kontrolek w stylu klasycznym Windows, który może utrudnić Utrzymaj spójne środowisko interfejsu użytkownika po włączeniu rysowania formantów niestandardowych w aplikacjach przy użyciu stylów wizualnych.  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] Obejmuje klas w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw, renderowanie części i Stany wspólnych formantów przy użyciu stylów wizualnych. Każda z tych klas zawiera `static` metody służące do rysowania formantu lub części kontrolki w określonym stanie przy użyciu bieżącego stylu wizualnego systemu operacyjnego.  
  
 Niektóre z tych klas są przeznaczone do rysowania pokrewnej kontrolki, niezależnie od tego, czy są dostępne style wizualne. Po włączeniu funkcji stylów wizualnych następnie składowych klasy narysuje pokrewnej kontrolki przy użyciu stylów wizualnych; Wyłączenie funkcji stylów wizualnych składowych klasy będzie narysuj kontrolkę w stylu klasycznym Windows. W ramach tych zajęć, obejmują:  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Style wizualne są dostępne, gdy ich elementy członkowskie spowoduje zgłoszenie wyjątku, wyłączenie funkcji stylów wizualnych innych klas tylko rysować pokrewnej kontrolki. W ramach tych zajęć, obejmują:  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Aby uzyskać więcej informacji na temat korzystania z tych klas do rysowania kontrolki, zobacz [jak: Używanie klasy renderowania formantu](how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Elementu stylu wizualnego i renderowanie klas  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Przestrzeń nazw zawiera klasy, które mogą służyć do tworzenia oraz uzyskać informacje na temat dowolnego formantu lub elementu interfejsu użytkownika, który jest obsługiwany przez stylów wizualnych. Obsługiwane zawierają między innymi wspólnych formantów, które mają klasy renderowania w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw (zobacz poprzednią sekcję), a także inne formanty, takie jak formanty karty i kontrolki paska pomocniczego. Inne obsługiwane elementy interfejsu użytkownika obejmują części **Start** menu, pasek zadań, a także nieklienckim obszarze okna.  
  
 Głównych klas <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> nazw są <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> i <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> jest to klasa foundation, do identyfikacji dowolnego elementu interfejs kontroli lub użytkownika, obsługiwane przez stylów wizualnych. Oprócz <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> , <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeń nazw zawiera wiele klas zagnieżdżonych <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> z `static` właściwości, które zwracają <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> dla każdego stanu kontrolki, kontrola części lub innego elementu interfejsu użytkownika, obsługiwane przez visual style.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> udostępnia metody, rysowania, które zawiera informacje o każdej <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> zdefiniowane przez bieżącego stylu wizualnego systemu operacyjnego. Informacje, które mogą być pobierane dotyczące elementu obejmuje jego domyślny rozmiar, typ tła i koloru definicji. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> otacza funkcjonalność klasy stylów wizualnych (UxTheme) interfejsu API z powłoki Windows części zestawu SDK platformy Windows. Aby uzyskać więcej informacji, zobacz [Włączanie stylów wizualnych](/windows/desktop/controls/cookbook-overview).  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> i <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, zobacz [jak: Renderowanie elementu stylu wizualnego](how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Włączanie stylów wizualnych  
 Aby włączyć style wizualne dla aplikacji napisanych dla platformy .NET Framework w wersji 1.0, programiści mogą zawierać manifest aplikacji, która określa, że ComCtl32.dll w wersji 6 lub nowszym będzie służyć do rysowania formantów. Można użyć aplikacji utworzonych za pomocą programu .NET Framework w wersji 1.1 lub nowszej <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.Application> klasy.  
  
## <a name="checking-for-visual-styles-support"></a>Sprawdzanie, obsługę stylów wizualnych  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Właściwość <xref:System.Windows.Forms.Application> klasa wskazuje, czy bieżącej aplikacji rysowania formantów przy użyciu stylów wizualnych. Malowanie kontrolki niestandardowej, można sprawdzić wartość <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> do określenia, czy ma być renderowany kontrolki z lub bez stylów wizualnych. W poniższej tabeli przedstawiono cztery warunki, które musi istnieć przez <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> do zwrócenia `true`.  
  
|Warunek|Uwagi|  
|---------------|-----------|  
|System operacyjny obsługuje stylów wizualnych.|Aby sprawdzić ten warunek oddzielnie, użyj <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> właściwość <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> klasy.|  
|Użytkownik włączył stylów wizualnych w systemie operacyjnym.|Aby sprawdzić ten warunek oddzielnie, użyj <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> właściwość <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> klasy.|  
|Style wizualne są włączone w aplikacji.|Można włączyć style wizualne w aplikacji, wywołując <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody lub za pomocą aplikacji manifest, który określa, że wersja pliku ComCtl32.dll 6 lub nowszej będzie używany do rysowania formantów.|  
|Style wizualne są używane do rysowania obszaru klienckiego aplikacji systemu windows.|Aby sprawdzić ten warunek oddzielnie, użyj <xref:System.Windows.Forms.Application.VisualStyleState%2A> właściwość <xref:System.Windows.Forms.Application> klasy i sprawdź, czy wartość <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> lub <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Aby określić, kiedy użytkownik umożliwia powoduje wyłączenie funkcji stylów wizualnych lub zmienia się z jednego styl wizualny do innego, wyszukaj <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> wartość programy obsługi dla <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> lub <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> zdarzenia.  
  
> [!IMPORTANT]
>  Jeśli chcesz używać <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> do renderowania formantu lub elementu interfejsu użytkownika, gdy użytkownik włączy lub zmienia stylów wizualnych, upewnij się, to zrobić podczas obsługi <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń zamiast <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> zdarzeń. Wyjątek zostanie zgłoszony, jeśli używasz <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> klasy podczas obsługi <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Zobacz także

- [Malowanie i renderowanie kontrolki niestandardowej](custom-control-painting-and-rendering.md)
