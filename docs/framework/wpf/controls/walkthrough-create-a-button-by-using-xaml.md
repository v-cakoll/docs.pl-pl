---
title: "Wskazówki: Tworzenie przycisku przy użyciu XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c5efa9f8787e65d59e1b544632e806bf3fbbc81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Wskazówki: Tworzenie przycisku przy użyciu XAML
Celem tego przewodnika jest Dowiedz się, jak utworzyć animowany przycisk do użycia w [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacji. W tym przewodniku zastosowano style i szablon, aby utworzyć zasób dostosowany przycisk umożliwiający ponowne użycie kodu i oddzielenie logiki przycisk z deklaracji przycisku. W tym przewodniku są zapisywane w całości w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  W tym przewodniku prowadzi użytkownika przez kroki tworzenia aplikacji, wpisując lub kopiowanie i wklejanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Microsoft [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. Jeśli chcesz dowiedzieć się, jak używać narzędzia projektowe (Microsoft Expression Blend) do tworzenia tej samej aplikacji, zobacz [utworzyć przycisk przy użyciu Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 Na poniższej ilustracji przedstawiono Zakończono przycisków.  
  
 ![Przyciski niestandardowe, które zostały utworzone przy użyciu języka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Utwórz podstawowe przyciski  
 Zacznijmy od tworzenia nowego projektu i dodawanie przycisków kilka do okna.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Aby utworzyć nowy projekt WPF i dodawanie przycisków do okna  
  
1.  Uruchom[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
2.  **Utwórz nowy projekt WPF:** na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**. Znajdź **aplikacji systemu Windows (WPF)** szablonu i nazwy projektu "AnimatedButton". Spowoduje to utworzenie szkielet dla aplikacji.  
  
3.  **Dodawanie przycisków domyślna podstawowa:** wszystkie pliki, które są potrzebne w tym przewodniku są udostępniane przez szablon. Otwórz plik Window1.xaml przez dwukrotne kliknięcie go w Eksploratorze rozwiązań. Domyślnie jest <xref:System.Windows.Controls.Grid> element Window1.xaml. Usuń <xref:System.Windows.Controls.Grid> element i dodaj kilka przycisków [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, wpisując lub kopiowania i wklejania następujący wyróżniony kod, aby Window1.xaml:  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">   <!-- Buttons arranged vertically inside a StackPanel. -->   <StackPanel HorizontalAlignment="Left">     <Button>Button 1</Button>     <Button>Button 2</Button>     <Button>Button 3</Button>   </StackPanel>  
  
    </Window>  
    ```  
  
     Naciśnij klawisz F5, aby uruchomić tej aplikacji; powinny pojawić się zestaw przycisków, która wygląda podobnie do poniższej ilustracji.  
  
     ![Trzy podstawowe przyciski](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     Teraz, po utworzeniu podstawowego przycisków, zakończeniu pracy w pliku Window1.xaml. Pozostałej części przewodnika skupiono się w pliku app.xaml, definiowania stylów i szablon przycisków.  
  
## <a name="set-basic-properties"></a>Właściwości podstawowe  
 Następnie umożliwia ustawienie kilku właściwości tych przycisków, aby kontrolować wygląd przycisku i układu. Zamiast ustawienie właściwości na przyciskach oddzielnie zasobów użyje do definiowania właściwości przycisku dla całej aplikacji. Zasoby aplikacji jest podobny do zewnętrznego [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] dla stron sieci Web; jednak zasoby są bardziej efektywne niż [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], jak widać na koniec tego przewodnika. Aby dowiedzieć się więcej na temat zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Aby używać stylów do ustawiania podstawowych właściwości na przyciskach  
  
1.  **Zdefiniuj bloku Application.Resources:** Otwórz app.xaml i Dodaj następujący wyróżniony kod znaczników, jeśli nie jest już istnieje:  
  
    ```xaml  
    <Application x:Class="AnimatedButton.App"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      StartupUri="Window1.xaml"  
      >  
      <Application.Resources>
        <!-- Resources for the entire application can be defined here. -->
      </Application.Resources>  
    </Application>  
    ```  
  
     Zakres zasobów jest określana przez gdzie został zdefiniowany zasób. Definiowanie zasobów w `Application.Resources` w pliku app.xaml plik umożliwia zasobów do użycia w dowolnym miejscu w aplikacji. Aby dowiedzieć się więcej na temat definiowania zakresu zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
2.  **Tworzenie stylu oraz definiować wartości właściwości podstawowych z nim:** Dodaj następujący kod do `Application.Resources` bloku. Tworzy tego znacznika <xref:System.Windows.Style> dotyczy wszystkich przycisków w ustawienia aplikacji <xref:System.Windows.FrameworkElement.Width%2A> przycisków do 90 i <xref:System.Windows.FrameworkElement.Margin%2A> do 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> Właściwość określa, czy styl ma zastosowanie do wszystkich obiektów typu <xref:System.Windows.Controls.Button>. Każdy <xref:System.Windows.Setter> ustawia wartość inną właściwość <xref:System.Windows.Style>. W związku z tym w tym momencie co przycisk w aplikacji ma szerokość 90 i margines 10.  Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację, pojawi się następujące okna.  
  
     ![Przyciski szerokość 90 i margines 10](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     Jest znacznie więcej można zrobić za pomocą stylów, w tym na wiele sposobów w celu dopasowania, jakie obiekty są stosowane, określania wartości właściwości złożonej i nawet przy użyciu stylów jako dane wejściowe dla innych stylów. Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
3.  **Ustaw wartość właściwości stylu do zasobu:** zasobów włączyć ponownie użyć wartości często zdefiniowanych obiektów i w prosty sposób. Jest szczególnie przydatne określić wartości złożonych korzystanie z zasobów w celu uczynienia kodu więcej moduły. Dodaj następujący wyróżniony kod znaczników do pliku app.xaml.  
  
    ```xaml  
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush" StartPoint="0,0" EndPoint="1,1">
        <GradientStop Color="DarkGray" Offset="0" />
        <GradientStop Color="#CCCCFF" Offset="0.5" />
        <GradientStop Color="DarkGray" Offset="1" />
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
      </Style>  
    </Application.Resources>  
    ```  
  
     Bezpośrednio pod `Application.Resources` bloku, utworzony zasób o nazwie "GrayBlueGradientBrush". Ten zasób definiuje gradient poziomy. Ten zasób mogą być używane jako wartości właściwości z dowolnego miejsca w aplikacji, w tym wewnątrz metody ustawiającej styl przycisku dla <xref:System.Windows.Controls.Control.Background%2A> właściwości. Obecnie wszystkie przyciski musi <xref:System.Windows.Controls.Control.Background%2A> wartość właściwości to gradientu.  
  
     Naciśnij klawisz F5, aby uruchomić aplikację. Jego wygląd powinien być podobne do następujących.  
  
     ![Przyciski gradientu tła](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Tworzenie szablonu, która definiuje wygląd przycisku  
 W tej sekcji możesz utworzyć szablon, który dostosowuje wygląd przycisku (prezentacja). Prezentacja przycisk składa się z kilku obiektów w tym prostokąty i inne składniki umożliwiają unikatowy wygląd przycisku.  
  
 Do tej pory kontrolę nad wygląd przycisków w aplikacji ma została ograniczona do zmiana właściwości przycisku. Co zrobić, jeśli chcesz dokonać bardziej znaczące zmiany wygląd przycisku? Szablony włączyć zaawansowaną kontrolę nad prezentacji obiektu. Ponieważ szablony mogą być używane w ramach stylów, można zastosować szablonu do wszystkich obiektów, których styl dotyczy (w tym przewodniku przycisku).  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Aby użyć szablonu, aby określić wygląd przycisku  
  
1.  **Konfigurowanie szablonu:** ponieważ formantów, takich jak <xref:System.Windows.Controls.Button> ma <xref:System.Windows.Controls.Control.Template%2A> właściwości, można zdefiniować wartości właściwości szablonu, podobnie jak inne wartości właściwości ustawiliśmy w <xref:System.Windows.Style> przy użyciu <xref:System.Windows.Setter>. Dodaj następujący wyróżniony kod znaczników do własnego stylu przycisku.  
  
    ```xaml
    <Application.Resources>  
      <LinearGradientBrush x:Key="GrayBlueGradientBrush"   
        StartPoint="0,0" EndPoint="1,1">  
        <GradientStop Color="DarkGray" Offset="0" />  
        <GradientStop Color="#CCCCFF" Offset="0.5" />  
        <GradientStop Color="DarkGray" Offset="1" />  
      </LinearGradientBrush>  
      <Style TargetType="{x:Type Button}">  
        <Setter Property="Background" Value="{StaticResource GrayBlueGradientBrush}" />  
        <Setter Property="Width" Value="80" />  
        <Setter Property="Margin" Value="10" />  
        <Setter Property="Template">
          <Setter.Value>
            <!-- The button template is defined here. -->
          </Setter.Value>
        </Setter>  
      </Style>  
    </Application.Resources>  
    ```  
  
2.  **ALTER prezentacji przycisku:** na tym etapie należy zdefiniować w szablonie. Dodaj następujący wyróżniony kod znaczników. Ten kod znaczników określa dwa <xref:System.Windows.Shapes.Rectangle> elementy z zaokrąglonymi narożnikami, a następnie <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.DockPanel> Służy do hosta <xref:System.Windows.Controls.ContentPresenter> przycisku. A <xref:System.Windows.Controls.ContentPresenter> Wyświetla zawartość przycisku. W tym przewodniku zawartość jest tekst ("1 przycisk", "Przycisk 2", "Przycisk 3"). Wszystkie składniki szablonu (prostokątów i <xref:System.Windows.Controls.DockPanel>) są układane wewnątrz <xref:System.Windows.Controls.Grid>.  
  
    ```xaml  
    <Setter.Value>  
      <ControlTemplate TargetType="Button">
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}" ClipToBounds="True">
          <!-- Outer Rectangle with rounded corners. -->
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}" RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />
          <!-- Inner Rectangle with rounded corners. -->
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20" Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />
          <!-- Present Content (text) of the button. -->
          <DockPanel Name="myContentPresenterDockPanel">
            <ContentPresenter x:Name="myContentPresenter" Margin="20" Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />
          </DockPanel>
        </Grid>
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Naciśnij klawisz F5, aby uruchomić aplikację. Jego wygląd powinien być podobne do następujących.  
  
     ![](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3.  **Dodawanie do szablonu glasseffect:** obok doda szkła. Najpierw należy utworzyć kilka Tworzenie gradientu efekt szkła zasobów. Dodaj te gradientu zasobów dowolne miejsce w `Application.Resources` bloku:  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">     <GradientStop Color="WhiteSmoke" Offset="0.2" />     <GradientStop Color="Transparent" Offset="0.4" />     <GradientStop Color="WhiteSmoke" Offset="0.5" />     <GradientStop Color="Transparent" Offset="0.75" />     <GradientStop Color="WhiteSmoke" Offset="0.9" />     <GradientStop Color="Transparent" Offset="1" />   </GradientStopCollection>   <LinearGradientBrush x:Key="MyGlassBrushResource"     StartPoint="0,0" EndPoint="1,1" Opacity="0.75"     GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     Te zasoby są używane jako <xref:System.Windows.Shapes.Shape.Fill%2A> dla prostokąt NAS wstawianie do <xref:System.Windows.Controls.Grid> szablonu przycisku. Dodaj następujący wyróżniony kod znaczników do szablonu.  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}" Height="{TemplateBinding Height}"  
    ClipToBounds="True">  
  
        <!-- Outer Rectangle with rounded corners. -->  
        <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
        <!-- Inner Rectangle with rounded corners. -->  
        <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="Transparent" StrokeThickness="20"   
          Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20" />  
  
        <!-- Glass Rectangle -->     <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"       VerticalAlignment="Stretch"       StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"       Fill="{StaticResource MyGlassBrushResource}"       RenderTransformOrigin="0.5,0.5">       <Rectangle.Stroke>         <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">           <LinearGradientBrush.GradientStops>             <GradientStop Offset="0.0" Color="LightBlue" />             <GradientStop Offset="1.0" Color="Gray" />           </LinearGradientBrush.GradientStops>         </LinearGradientBrush>       </Rectangle.Stroke>       <!-- These transforms have no effect as they are declared here.             The reason the transforms are included is to be targets             for animation (see later). -->       <Rectangle.RenderTransform>         <TransformGroup>           <ScaleTransform />           <RotateTransform />         </TransformGroup>       </Rectangle.RenderTransform>       <!-- A BevelBitmapEffect is applied to give the button a             "Beveled" look. -->       <Rectangle.BitmapEffect>         <BevelBitmapEffect />       </Rectangle.BitmapEffect>     </Rectangle>  
  
        <!-- Present Text of the button. -->  
        <DockPanel Name="myContentPresenterDockPanel">  
          <ContentPresenter x:Name="myContentPresenter" Margin="20"   
            Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
        </DockPanel>  
      </Grid>  
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Zwróć uwagę, że <xref:System.Windows.UIElement.Opacity%2A> prostokąta z `x:Name` właściwości "glassCube" ma wartość 0, więc po uruchomieniu próbki nie ma prostokąt szkła umieszczenia w górnej części. Jest to spowodowane później dodamy Wyzwalacze w szablonie dla gdy użytkownik użyje przycisku. Jednak widoczny przycisk wygląd teraz zmieniając <xref:System.Windows.UIElement.Opacity%2A> wartości 1 i uruchamiania aplikacji. Zobacz poniższą ilustrację. Przed przejściem do następnego kroku, zmień <xref:System.Windows.UIElement.Opacity%2A> do 0.  
  
     ![Przyciski niestandardowe, które zostały utworzone przy użyciu języka XAML](../../../../docs/framework/wpf/controls/media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Utwórz interakcyjności przycisku  
 W tej sekcji utworzysz wyzwalaczy właściwości i wyzwalacze zdarzeń zmiany wartości właściwości i uruchomić animacji w odpowiedzi na działania użytkownika, takie jak wskaźnika myszy nad przyciskiem i kliknięcie przycisku.  
  
 Łatwe dodawanie interakcyjności (myszą, pozostaw myszy, kliknij przycisk itd.) jest zdefiniuj Wyzwalacze w stylu lub szablonie. Aby utworzyć <xref:System.Windows.Trigger>, takich jak zdefiniować właściwości "warunku": przycisk <xref:System.Windows.UIElement.IsMouseOver%2A> wartość właściwości jest równa `true`. Następnie zdefiniuj ustawiające (Akcje), które mają miejsce, gdy spełniony jest warunek wyzwalacza.  
  
#### <a name="to-create-button-interactivity"></a>Aby utworzyć interakcyjności przycisku  
  
1.  **Dodaj szablon wyzwalaczy:** Dodaj wyróżnione znaczników do szablonu.  
  
    ```  
    <Setter.Value>  
      <ControlTemplate TargetType="{x:Type Button}">  
        <Grid Width="{TemplateBinding Width}"   
          Height="{TemplateBinding Height}" ClipToBounds="True">  
  
          <!-- Outer Rectangle with rounded corners. -->  
          <Rectangle x:Name="outerRectangle" HorizontalAlignment="Stretch"   
          VerticalAlignment="Stretch" Stroke="{TemplateBinding Background}"   
          RadiusX="20" RadiusY="20" StrokeThickness="5" Fill="Transparent" />  
  
          <!-- Inner Rectangle with rounded corners. -->  
          <Rectangle x:Name="innerRectangle" HorizontalAlignment="Stretch"   
            VerticalAlignment="Stretch" Stroke="Transparent"   
            StrokeThickness="20"   
            Fill="{TemplateBinding Background}" RadiusX="20" RadiusY="20"   
          />  
  
          <!-- Glass Rectangle -->  
          <Rectangle x:Name="glassCube" HorizontalAlignment="Stretch"  
            VerticalAlignment="Stretch"  
            StrokeThickness="2" RadiusX="10" RadiusY="10" Opacity="0"  
            Fill="{StaticResource MyGlassBrushResource}"  
            RenderTransformOrigin="0.5,0.5">  
            <Rectangle.Stroke>  
              <LinearGradientBrush StartPoint="0.5,0" EndPoint="0.5,1">  
                <LinearGradientBrush.GradientStops>  
                  <GradientStop Offset="0.0" Color="LightBlue" />  
                  <GradientStop Offset="1.0" Color="Gray" />  
                </LinearGradientBrush.GradientStops>  
              </LinearGradientBrush>  
            </Rectangle.Stroke>  
  
            <!-- These transforms have no effect as they   
                 are declared here.   
                 The reason the transforms are included is to be targets   
                 for animation (see later). -->  
            <Rectangle.RenderTransform>  
              <TransformGroup>  
                <ScaleTransform />  
                <RotateTransform />  
              </TransformGroup>  
            </Rectangle.RenderTransform>  
  
              <!-- A BevelBitmapEffect is applied to give the button a   
                   "Beveled" look. -->  
            <Rectangle.BitmapEffect>  
              <BevelBitmapEffect />  
            </Rectangle.BitmapEffect>  
          </Rectangle>  
  
          <!-- Present Text of the button. -->  
          <DockPanel Name="myContentPresenterDockPanel">  
            <ContentPresenter x:Name="myContentPresenter" Margin="20"   
              Content="{TemplateBinding  Content}" TextBlock.Foreground="Black" />  
          </DockPanel>  
        </Grid>  
  
        <ControlTemplate.Triggers>       <!-- Set action triggers for the buttons and define            what the button does in response to those triggers. -->     </ControlTemplate.Triggers>  
      </ControlTemplate>  
    </Setter.Value>  
    ```  
  
2.  **Dodaj właściwość wyzwalaczy:** Dodaj wyróżnione znaczników `ControlTemplate.Triggers` bloku:  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Naciśnij klawisz F5, aby uruchomić aplikację i zobaczyć efekt, jak uruchomić wskaźnik myszy nad przycisków.  
  
3.  **Dodaj wyzwalacz fokus:** następnie dodamy pewnych ustawiające podobne do obsługi w przypadku, gdy przycisk ma fokus (na przykład po kliknięciu przez użytkownika).  
  
    ```  
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->  
      <Trigger Property="IsMouseOver" Value="True">  
  
        <!-- Below are three property settings that occur when the   
             condition is met (user mouses over button).  -->  
        <!-- Change the color of the outer rectangle when user          mouses over it. -->  
        <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"  
          Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />  
  
        <!-- Sets the glass opacity to 1, therefore, the          glass "appears" when user mouses over it. -->  
        <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />  
  
        <!-- Makes the text slightly blurry as though you were          looking at it through blurry glass. -->  
        <Setter Property="ContentPresenter.BitmapEffect"       TargetName="myContentPresenter">  
          <Setter.Value>  
            <BlurBitmapEffect Radius="1" />  
          </Setter.Value>  
        </Setter>  
      </Trigger>  
      <!-- Set properties when button has focus. -->   <Trigger Property="IsFocused" Value="true">     <Setter Property="Rectangle.Opacity" Value="1"       TargetName="glassCube" />     <Setter Property="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />   </Trigger>  
  
    </ControlTemplate.Triggers>  
    ```  
  
     Naciśnij klawisz F5, aby uruchomić aplikację i kliknij jeden z przycisków. Zwróć uwagę, czy przycisk pozostaje wyróżnione po kliknięciu, ponieważ nadal ma fokus. Jeśli klikniesz przycisk inny przycisk Nowy zyskuje fokus podczas ostatnią utraci go.  
  
4.  **Dodawanie animacji do** <xref:System.Windows.UIElement.MouseEnter> **i** <xref:System.Windows.UIElement.MouseLeave> **:** obok dodamy niektórych animacji wyzwalacze. Dodaj następujący kod w dowolnym miejscu wewnątrz elementu `ControlTemplate.Triggers` bloku.  
  
    ```  
    <!-- Animations that start when mouse enters and leaves button. -->  
    <EventTrigger RoutedEvent="Mouse.MouseEnter">  
      <EventTrigger.Actions>  
        <BeginStoryboard Name="mouseEnterBeginStoryboard">  
          <Storyboard>  
          <!-- This animation makes the glass rectangle shrink in the X direction. -->  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleX)"  
              By="-0.1" Duration="0:0:0.5" />  
            <!-- This animation makes the glass rectangle shrink in the Y direction. -->  
            <DoubleAnimation  
            Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[0].(ScaleTransform.ScaleY)"   
              By="-0.1" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    <EventTrigger RoutedEvent="Mouse.MouseLeave">  
      <EventTrigger.Actions>  
        <!-- Stopping the storyboard sets all animated properties back to default. -->  
        <StopStoryboard BeginStoryboardName="mouseEnterBeginStoryboard" />  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     Prostokąt szkła zmniejszana, gdy wskaźnik myszy przesuwa się nad przyciskiem i zwraca powrót do normalnego rozmiaru, gdy wskaźnik myszy opuści.  
  
     Istnieją dwa animacji, które są wyzwalane, gdy wskaźnik myszy nad przyciskiem (<xref:System.Windows.UIElement.MouseEnter> zdarzenia). Te animacje zmniejszyć prostokąt szkła wzdłuż osi X i Y. Zauważ, że właściwości na <xref:System.Windows.Media.Animation.DoubleAnimation> elementy — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Określa animacji ponad pół sekundy, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Określa, że szkła zmniejsza przy 10%.  
  
     Drugi wyzwalacza zdarzenia (<xref:System.Windows.UIElement.MouseLeave>) po prostu zatrzymuje pierwsza z nich. Po zatrzymaniu <xref:System.Windows.Media.Animation.Storyboard>, animowanej właściwości powrócić do wartości domyślnych. W związku z tym gdy użytkownik przesuwa kursor poza przycisk, przycisk powraca sposób przed wskaźnik myszy jest przesuwany nad przycisku. Aby uzyskać więcej informacji na temat animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
5.  **Dodaj animację po kliknięciu przycisku:** ostatnim krokiem jest dodanie wyzwalacz po kliknięciu przycisku. Dodaj następujący kod w dowolnym miejscu wewnątrz elementu `ControlTemplate.Triggers` bloku:  
  
    ```  
    <!-- Animation fires when button is clicked, causing glass to spin.  -->  
    <EventTrigger RoutedEvent="Button.Click">  
      <EventTrigger.Actions>  
        <BeginStoryboard>  
          <Storyboard>  
            <DoubleAnimation Storyboard.TargetName="glassCube"   
              Storyboard.TargetProperty=  
              "(Rectangle.RenderTransform).(TransformGroup.Children)[1].(RotateTransform.Angle)"   
              By="360" Duration="0:0:0.5" />  
          </Storyboard>  
        </BeginStoryboard>  
      </EventTrigger.Actions>  
    </EventTrigger>  
    ```  
  
     Naciśnij klawisz F5, aby uruchomić aplikację i kliknij jeden z przycisków. Po kliknięciu przycisku prostokąt szkła obraca się wokół.  
  
## <a name="summary"></a>Podsumowanie  
 W tym przewodniku wykonywane są następujące ćwiczeń:  
  
-   Celem <xref:System.Windows.Style> z typem obiektu (<xref:System.Windows.Controls.Button>).  
  
-   Kontrolowane podstawowe właściwości przycisków w całej aplikacji przy użyciu <xref:System.Windows.Style>.  
  
-   Utworzone zasoby, takie jak gradientów do użycia dla wartości właściwości <xref:System.Windows.Style> setters.  
  
-   Dostosować wygląd przycisków w całej aplikacji przez zastosowanie szablonu do przycisków.  
  
-   Dostosowywać zachowanie w przypadku przycisków, w odpowiedzi na działania użytkownika (takich jak <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, i <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) które zawarte efekty animacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie przycisku przy użyciu programu Microsoft Expression Blend](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Efekty mapy bitowej — przegląd](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)
