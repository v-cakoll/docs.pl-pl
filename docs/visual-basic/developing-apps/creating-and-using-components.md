---
title: Tworzenie szablonów i korzystanie z nich
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: 2fefdff9dc27915066e3d92efd8439adffed9fc5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330297"
---
# <a name="creating-and-using-components-in-visual-basic"></a>Tworzenie składników i korzystanie z nich w Visual Basic

*Składnik* jest klasą, która implementuje interfejs <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> lub który dziedziczy bezpośrednio lub pośrednio z klasy implementującej <xref:System.ComponentModel.IComponent>. Składnik .NET Framework jest obiektem, który jest wielokrotnego użytku, może współdziałać z innymi obiektami i zapewnia kontrolę nad zasobami zewnętrznymi i obsługą czasu projektowania.  
  
 Ważną cechą składników jest możliwość projektowania, co oznacza, że Klasa, która jest składnikiem, może być używana w zintegrowanym środowisku programistycznym programu Visual Studio. Składnik może być dodany do przybornika, przeciągany i upuszczany na formularz oraz do manipulowania na powierzchni projektowej. Należy zauważyć, że podstawowa obsługa w czasie projektowania składników jest wbudowana w .NET Framework; deweloper składnika nie musi wykonywać żadnych dodatkowych czynności, aby korzystać z podstawowych funkcji czasu projektowania.  
  
 *Kontrolka* jest podobna do składnika, zarówno do projektowania. Jednak formant udostępnia interfejs użytkownika, natomiast składnik nie jest. Kontrolka musi pochodzić od jednej z klas podstawowego formantu: <xref:System.Windows.Forms.Control> lub <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Kiedy należy utworzyć składnik  

 Jeśli Klasa zostanie użyta na powierzchni projektowej (takiej jak Windows Forms lub Projektant formularzy Web Forms), ale nie ma interfejsu użytkownika, powinien być składnikiem i implementować <xref:System.ComponentModel.IComponent>lub dziedziczyć z klasy, która bezpośrednio lub pośrednio implementuje <xref:System.ComponentModel.IComponent>.  
  
 Klasy <xref:System.ComponentModel.Component> i <xref:System.ComponentModel.MarshalByValueComponent> są podstawowymi implementacjami interfejsu <xref:System.ComponentModel.IComponent>. Główna różnica między tymi klasami polega na tym, że Klasa <xref:System.ComponentModel.Component> jest organizowana przez odwołanie, podczas gdy <xref:System.ComponentModel.IComponent> jest organizowane przez wartość. Poniższa lista zawiera szczegółowe wskazówki dotyczące implementacji.  
  
- Jeśli składnik musi być zorganizowany przez odwołanie, pochodzi od <xref:System.ComponentModel.Component>.  
  
- Jeśli składnik musi być zorganizowany przez wartość, pochodny od <xref:System.ComponentModel.MarshalByValueComponent>.  
  
- Jeśli składnik nie może pochodzić z jednej z implementacji podstawowych z powodu pojedynczego dziedziczenia, zaimplementuj <xref:System.ComponentModel.IComponent>.  
  
## <a name="component-classes"></a>Klasy składników  

 Przestrzeń nazw <xref:System.ComponentModel> zawiera klasy, które są używane do implementowania działania składników i formantów w czasie wykonywania oraz w czasie projektowania. Ta przestrzeń nazw zawiera klasy bazowe i interfejsy służące do implementowania atrybutów i konwerterów typów, powiązania ze źródłami danych i składnikami licencjonowania.  
  
 Podstawowe klasy składników to:  
  
- <xref:System.ComponentModel.Component>., Podstawowa implementacja interfejsu <xref:System.ComponentModel.IComponent>. Ta klasa umożliwia udostępnianie obiektów między aplikacjami.  
  
- <xref:System.ComponentModel.MarshalByValueComponent>., Podstawowa implementacja interfejsu <xref:System.ComponentModel.IComponent>.  
  
- <xref:System.ComponentModel.Container>., Podstawowa implementacja interfejsu <xref:System.ComponentModel.IContainer>. Ta klasa hermetyzuje zero lub więcej składników.  
  
 Niektóre klasy używane do licencjonowania składników są następujące:  
  
- <xref:System.ComponentModel.License>., Abstrakcyjna klasa bazowa dla wszystkich licencji. Licencja jest udzielana do określonego wystąpienia składnika.  
  
- <xref:System.ComponentModel.LicenseManager>., Zawiera właściwości i metody umożliwiające dodanie licencji do składnika oraz zarządzanie <xref:System.ComponentModel.LicenseProvider>.  
  
- <xref:System.ComponentModel.LicenseProvider>., Abstrakcyjna klasa bazowa służąca do implementowania dostawcy licencji.  
  
- <xref:System.ComponentModel.LicenseProviderAttribute>., Określa klasę <xref:System.ComponentModel.LicenseProvider>, która ma być używana z klasą.  
  
 Klasy często używane do opisywania i utrwalania składników.  
  
- <xref:System.ComponentModel.TypeDescriptor>., Zawiera informacje o charakterystyce składnika, takie jak jego atrybuty, właściwości i zdarzenia.  
  
- <xref:System.ComponentModel.EventDescriptor>., Zawiera informacje o zdarzeniu.  
  
- <xref:System.ComponentModel.PropertyDescriptor>., Zawiera informacje o właściwości.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

 [Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Wyjaśnia, jak rozwiązać typowe problemy.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: uzyskiwanie dostępu do obsługi czasu projektowania w programie Windows Forms](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
