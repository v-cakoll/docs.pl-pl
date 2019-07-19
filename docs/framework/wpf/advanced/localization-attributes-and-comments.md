---
title: Lokalizacja atrybutów i komentarzy
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 1ef18802ab3568df00e29eb4ccaf717f4bdf4863
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330999"
---
# <a name="localization-attributes-and-comments"></a>Lokalizacja atrybutów i komentarzy
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Komentarze do lokalizacji to właściwości [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] w kodzie źródłowym dostarczanym przez deweloperów w celu zapewnienia zasad i wskazówek dotyczących lokalizacji. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Komentarze dotyczące lokalizacji zawierają dwa zestawy informacji: atrybuty lokalizowania i komentarze do lokalizacji w dowolnej postaci. Atrybuty umożliwiające zlokalizowanie są używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejs API lokalizacji, aby wskazać, które zasoby mają być lokalizowane. Komentarze w formie bezpłatnej są dowolnymi informacjami, które autor aplikacji chce uwzględnić.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Komentarze dotyczące lokalizacji  
 Jeśli autorzy aplikacji znaczników mają wymagania dotyczące określonych elementów [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]w, takich jak ograniczenia dotyczące długości tekstu, rodziny czcionek lub rozmiaru czcionki, mogą przekazać te informacje do lokalizatorów z komentarzami [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] w kodzie. Proces dodawania komentarzy do kodu źródłowego jest następujący:  
  
1. Deweloper aplikacji dodaje Komentarze do [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] lokalizacji kodu źródłowego.  
  
2. W trakcie procesu kompilowania można określić w pliku. proj, czy pozostawić Komentarze do lokalizacji dowolnego formularza w zestawie, przydzielić część komentarzy lub wszystkie komentarze. Usunięte komentarze są umieszczane w osobnym pliku. Należy określić opcję przy użyciu `LocalizationDirectivesToLocFile` znacznika, np.:  
  
     `<LocalizationDirectivesToLocFile>`*wartość*`</LocalizationDirectivesToLocFile>`  
  
3. Wartości, które można przypisać:  
  
    - **Brak** — Komentarze i atrybuty pozostają wewnątrz zestawu i nie jest generowany żaden oddzielny plik.  
  
    - **CommentsOnly** — łączy tylko komentarze z zestawu i umieszcza je w osobnym LocFile.  
  
    - **Wszystkie** -paski komentarzy i atrybuty z zestawu i umieszcza je w osobnym LocFile.  
  
4. Gdy lokalizowalne zasoby są wyodrębniane z BAML, atrybuty lokalizowania są przestrzegane przez interfejs API lokalizacji BAML.  
  
5. Pliki komentarzy do lokalizacji zawierające tylko komentarze w formie dowolnego formularza są włączane w procesie lokalizowania w późniejszym czasie.  
  
 Poniższy przykład pokazuje, jak dodać komentarze do lokalizacji do [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] pliku.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 W poprzednim przykładzie sekcja lokalizacji. Attributes zawiera atrybuty lokalizacji i sekcję lokalizacja. Komentarze w formie bezpłatnych komentarzy. W poniższych tabelach przedstawiono atrybuty i komentarze oraz ich znaczenie dla lokalizatora.  
  
|Atrybuty lokalizacji|Znaczenie|  
|-----------------------------|-------------|  
|$Content (niemodyfikowalny tekst do odczytu)|Zawartości elementu TextBlock nie można modyfikować. Lokalizatory nie mogą zmieniać wyrazu "Microsoft". Zawartość jest widoczna (czytelna) dla lokalizatora. Kategoria zawartości to tekst.|  
|FontFamily (niemodyfikowalny do odczytu)|Nie można zmienić właściwości rodziny czcionek elementu TextBlock, ale jest ona widoczna dla lokalizatora.|  
  
|Niezależne komentarze dotyczące lokalizacji|Znaczenie|  
|--------------------------------------|-------------|  
|$Content (znak towarowy)|Autor aplikacji instruuje lokalizatora, że zawartość w elemencie TextBlock jest znakiem towarowym.|  
|FontSize (rozmiar czcionki znaku towarowego)|Autor aplikacji wskazuje, że właściwość rozmiar czcionki powinna być zgodna ze standardowym rozmiarem znaku towarowego.|  
  
### <a name="localizability-attributes"></a>Atrybuty lokalizacji  
 Informacje w lokalizacji. atrybuty zawierają listę par: Nazwa wartości dostosowanej i skojarzone wartości do zlokalizowania. Nazwa elementu docelowego może być nazwą właściwości lub specjalną nazwą $Content. Jeśli jest to nazwa właściwości, wartość domowa jest wartością właściwości. Jeśli jest $Content, wartość docelowa to zawartość elementu.  
  
 Istnieją trzy typy atrybutów:  
  
- **Kategoria**. Określa, czy wartość powinna być modyfikowalna z narzędzia zlokalizowanego. Zobacz <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Czytelność**. Określa, czy narzędzie do lokalizowania ma odczytywać (i wyświetlać) wartość. Zobacz <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Modifiability**. Określa, czy narzędzie do lokalizowania pozwala na modyfikowanie wartości. Zobacz <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Te atrybuty można określić w dowolnej kolejności ograniczonej spacją. W przypadku określenia zduplikowanych atrybutów ostatni atrybut przesłoni poprzednie. Na przykład lokalizacja. atrybuty = "niemodyfikowane modyfikowalne" ustawia modifiability na modyfikowalny, ponieważ jest ostatnią wartością.  
  
 Modifiability i czytelność nie mają wyjaśnień. Atrybut kategorii zawiera wstępnie zdefiniowane kategorie, które pomagają lokalizatorowi podczas tłumaczenia tekstu. Kategorie, takie jak, tekst, etykieta i tytuł, umożliwiają zlokalizowanie informacji o sposobie tłumaczenia tekstu. Istnieją również specjalne kategorie: None, inherit, ignore i NeverLocalize.  
  
 W poniższej tabeli przedstawiono znaczenie specjalnych kategorii.  
  
|Kategoria|Znaczenie|  
|--------------|-------------|  
|Brak|Wartość domowa nie ma zdefiniowanej kategorii.|  
|Odziedziczony|Wartość docelowa dziedziczy jej kategorię z jej elementu nadrzędnego.|  
|Zignoruj|Wartość domowa jest ignorowana w procesie lokalizacji. Wartość Ignoruj dotyczy tylko bieżącej wartości. Nie wpłynie to na węzły podrzędne.|  
|NeverLocalize|Nie można lokalizować bieżącej wartości. Ta kategoria jest dziedziczona przez elementy podrzędne elementu.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Komentarze dotyczące lokalizacji  
 Lokalizacja. Komentarze zawierają ciągi o dowolnej postaci dotyczące wartości dostosowanej. Deweloperzy aplikacji mogą dodawać informacje w celu uzyskania wskazówek dla lokalizatorów o sposobie tłumaczenia tekstu aplikacji. Format komentarzy może być dowolnym ciągiem, który jest ujęty w znak "()". Użyj znaku\\"" do znaków ucieczki.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizacja dla WPF](globalization-for-wpf.md)
- [Używanie automatycznego układu do utworzenia przycisku](how-to-use-automatic-layout-to-create-a-button.md)
- [Używanie siatki do automatycznego układu](how-to-use-a-grid-for-automatic-layout.md)
- [Lokalizowanie aplikacji](how-to-localize-an-application.md)
