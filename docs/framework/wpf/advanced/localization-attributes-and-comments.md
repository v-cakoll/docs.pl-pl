---
title: Lokalizacja atrybutów i komentarzy
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 7cfcc9fa4dc3bc1450febb39500b7d96f92beac6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="localization-attributes-and-comments"></a>Lokalizacja atrybutów i komentarzy
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Lokalizacja komentarze są właściwościami, wewnątrz [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kod źródłowy, dostarczone przez deweloperów do zapewnienia lokalizacji zasad i wskazówek dotyczących serwerów. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Lokalizacja komentarze zawierają dwa zestawy informacji: atrybuty możliwości zlokalizowania i lokalizacja dowolne komentarze. Możliwość lokalizacji atrybuty są używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizacja interfejsu API, aby wskazać, zasobów, do których mają być lokalizowany. Dowolne komentarze są wszystkie informacje, które chce dołączyć Autor aplikacji.  
  

  
<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Komentarze w lokalizacji  
 Jeśli znaczników aplikacji Autorzy mają wymagania dotyczące określonych elementów w [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], takie jak ograniczenia dotyczące długość tekstu rodziny czcionek i rozmiar czcionki, ich przedstawienia tych informacji, aby wiadomość dla lokalizatorów z uwagi na [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kodu. Proces dodawania komentarzy do kodu źródłowego, jest następujący:  
  
1.  Deweloper aplikacji dodaje komentarz lokalizacji do [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kod źródłowy.  
  
2.  Podczas procesu kompilacji można określić w pliku .proj czy należy pozostawić komentarze dowolnych lokalizacji zestawu, paska się częścią komentarze lub paska limit wszystkie komentarze. Komentarze usunięta poza są umieszczane w oddzielnym pliku. Można ją określić za pomocą opcji `LocalizationDirectivesToLocFile` tagu np:  
  
     `<LocalizationDirectivesToLocFile>` *Wartość* `</LocalizationDirectivesToLocFile>`  
  
3.  Dostępne są następujące wartości, które można przypisać:  
  
    -   **Brak** -komentarzy i atrybutów pozostają w zestawie, a ten sam plik jest generowany.  
  
    -   **CommentsOnly** — usuwa tylko komentarze z zestawu i umieszcza je w oddzielne LocFile.  
  
    -   **Wszystkie** — usuwa zarówno komentarzy i atrybutów z zestawu i umieszcza je w oddzielne LocFile.  
  
4.  Gdy zlokalizowania zasobów są wyodrębniane z [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], atrybuty możliwości zlokalizowania są przestrzegane przez [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] lokalizacja interfejsu API.  
  
5.  Pliki komentarza lokalizacji, zawierający tylko dowolne komentarze są włączone w procesie lokalizacji w późniejszym czasie.  
  
 Poniższy przykład przedstawia sposób dodawać komentarze lokalizacja [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 W poprzednim przykładzie Localization.Attributes sekcja zawiera atrybuty lokalizacji i komentarze sekcji dowolnych Localization.Comments. W poniższej tabeli przedstawiono atrybuty i komentarze i ich znaczenie do lokalizatora.  
  
|Atrybuty lokalizacji|Znaczenie|  
|-----------------------------|-------------|  
|$Content (unmodifiable czytelnej)|Nie można zmodyfikować zawartość elementu blok tekstu. Wiadomość dla lokalizatorów nie można zmienić słowa "Microsoft". Zawartość jest widoczna (elementu Readable) do lokalizatora. Do kategorii zawartości jest tekst.|  
|FontFamily (Unmodifiable do odczytu)|Nie można zmienić właściwości rodziny czcionek elementu blok tekstu, ale jest widoczny dla lokalizatora.|  
  
|Lokalizacja dowolne komentarze|Znaczenie|  
|--------------------------------------|-------------|  
|$Content (znak towarowy)|Autor aplikacji lokalizatora informuje, że zawartość w elemencie blok tekstu jest zastrzeżonym znakiem towarowym firmy.|  
|FontSize (znak towarowy rozmiar czcionki)|Autor aplikacji wskazuje, że właściwość rozmiar czcionki, należy wykonać rozmiar znaków towarowych.|  
  
### <a name="localizability-attributes"></a>Możliwość lokalizacji atrybutów  
 Informacje zawarte w Localization.Attributes zawiera listę par: Nazwa docelowej wartości i wartości skojarzone możliwości zlokalizowania. Nazwa docelowego może być nazwa właściwości lub specjalną nazwą $Content. Jeśli jest to nazwa właściwości, wartość docelowa jest wartość właściwości. Jeśli jest $Content wartość docelowa jest zawartość elementu.  
  
 Istnieją trzy typy atrybutów:  
  
-   **Kategoria**. Określa, czy wartość należy modyfikować za pomocą narzędzia lokalizatora. Zobacz <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
-   **Czytelność**. Określa, czy narzędzie lokalizatora należy odczytać (i wyświetlić) wartość. Zobacz <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
-   **Modifiability**. To ustawienie określa, czy narzędzie lokalizatora daje wartość ma zostać zmodyfikowana. Zobacz <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Te atrybuty można określić w dowolnej kolejności rozdzielonych spacją. W przypadku, gdy określono zduplikowane atrybuty, ostatniego atrybutu spowoduje zastąpienie pierwszych. Na przykład Localization.Attributes = "Unmodifiable modyfikowalnymi" Ustawia Modifiability do Modifiable, ponieważ jest to ostatnia wartość.  
  
 Modifiability i czytelność nie wymaga wyjaśnień. Atrybut kategorii udostępnia wstępnie zdefiniowane kategorie ułatwiające lokalizatora podczas tłumaczenia tekstu. Kategorie, takie jak przyznanie tekst etykiety i tytuł lokalizatora informacje o sposobie tłumaczenie tekstu. Istnieje również specjalne kategorii: Brak, Dziedzicz Ignoruj i NeverLocalize.  
  
 W poniższej tabeli przedstawiono znaczenie specjalne kategorii.  
  
|Kategoria|Znaczenie|  
|--------------|-------------|  
|Brak|Wartość docelowa ma nie określonych kategorii.|  
|Dziedziczenie|Wartość docelowa dziedziczy kategorii po swoim obiekcie nadrzędnym.|  
|Ignoruj|Wartość docelowa jest ignorowany w procesie lokalizacji. Ignoruj dotyczy tylko bieżącej wartości. Nie wpłynie węzłów podrzędnych.|  
|NeverLocalize|Bieżąca wartość nie może być lokalizowany. Ta kategoria jest dziedziczona przez elementy podrzędne danego elementu.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Komentarze w lokalizacji  
 Localization.Comments zawiera dowolnych ciągów dotyczące wartości docelowych. Deweloperzy aplikacji można dodać informacje umożliwiają wiadomość dla lokalizatorów podpowiedź sposób przekształcania tekstu aplikacji. Format komentarzy może być dowolnym ciągiem otoczona "()". Użyj "\\' Aby wprowadzić znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Globalizacja dla WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Używanie automatycznego układu do utworzenia przycisku](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Używanie siatki do automatycznego układu](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)  
 [Lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
