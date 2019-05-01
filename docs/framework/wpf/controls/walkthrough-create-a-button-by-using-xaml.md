---
title: 'Przewodnik: Tworzenie przycisku przy użyciu języka XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 908a38485c879e3f28399bb7dbc8303afd4505da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024019"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Przewodnik: Tworzenie przycisku przy użyciu języka XAML
Celem tego przewodnika jest Dowiedz się, jak utworzyć przycisk animowany do użycia w aplikacji Windows Presentation Foundation (WPF). W tym przewodniku używa szablonu i style w celu utworzenia zasobu dostosowany przycisk, który umożliwia oddzielenie logiki przycisk od deklaracji przycisku i ponowne użycie kodu. W tym przewodniku są zapisywane w całości w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
> [!IMPORTANT]
>  Ten przewodnik przeprowadzi Cię przez kroki tworzenia aplikacji przez wpisanie lub kopiowanie i wklejanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do programu Microsoft Visual Studio. Jeśli chcesz użyć dowiedzieć się, jak używać narzędzia do projektowania (Microsoft Expression Blend) do tworzenia tej samej aplikacji, zobacz [tworzenie przycisku przy użyciu Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).  
  
 Na poniższej ilustracji przedstawiono Zakończono przycisków.  
  
 ![Przyciski niestandardowe, które zostały utworzone przy użyciu XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-basic-buttons"></a>Tworzenie przycisków podstawowe  
 Zacznijmy od utworzenia nowego projektu i dodanie kilku przycisków do okna.  
  
#### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Aby utworzyć nowy projekt WPF i dodać przyciski do okna  
  
1. Uruchom program Visual Studio.  
  
2. **Utwórz nowy projekt WPF:** Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**. Znajdź **Windows aplikacji (WPF)** szablonu i nazwy projektu "AnimatedButton". Spowoduje to utworzenie szkielet dla aplikacji.  
  
3. **Dodaj przyciski podstawowe domyślne:** Wszystkie pliki potrzebne w tym przewodniku znajdują się w szablonie. Otwórz plik Window1.xaml, klikając go dwukrotnie w Eksploratorze rozwiązań. Domyślnie jest <xref:System.Windows.Controls.Grid> element Window1.xaml. Usuń <xref:System.Windows.Controls.Grid> elementu i kilku przycisków, aby dodać [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony, wpisując lub skopiować i wkleić następujący wyróżniony kod do Window1.xaml:  
  
    ```xaml  
    <Window x:Class="AnimatedButton.Window1"  
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
      Title="AnimatedButton" Height="300" Width="300"   
      Background="Black">
      <!-- Buttons arranged vertically inside a StackPanel. -->
      <StackPanel HorizontalAlignment="Left">
          <Button>Button 1</Button>
          <Button>Button 2</Button>
          <Button>Button 3</Button>
      </StackPanel>  
    </Window>  
    ```  
  
     Naciśnij klawisz F5, aby uruchomić aplikację; powinien zostać wyświetlony zestaw przycisków, która wygląda podobnie do poniższej ilustracji.  
  
     ![Trzy podstawowe przyciski](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")  
  
     Teraz, po utworzeniu podstawowe przyciski, po zakończeniu pracy w pliku Window1.xaml. Pozostałe przewodnik koncentruje się na pliku app.xaml, definiowania stylów i szablonów dla przycisków.  
  
## <a name="set-basic-properties"></a>Ustawianie właściwości podstawowe  
 Następnie możemy ustawić niektóre właściwości na tych przycisków, aby kontrolować wyglądu przycisku i układu. Zamiast ustawienie właściwości na przyciskach oddzielnie, użyjesz zasobów do definiowania właściwości przycisku dla całej aplikacji. Zasoby aplikacji są koncepcyjnie podobne zewnętrznych [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)] dla stron sieci Web; jednak zasoby są znacznie bardziej zaawansowane niż [!INCLUDE[TLA#tla_css](../../../../includes/tlasharptla-css-md.md)], bo pozwoli zauważyć do końca tego przewodnika. Aby dowiedzieć się więcej na temat zasobów, zobacz [zasoby XAML](../advanced/xaml-resources.md).  
  
#### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Aby używać stylów do ustawiania właściwości podstawowe na przyciskach  
  
1. **Zdefiniuj blokiem Application.Resources:** Otwórz pliku app.xaml i Dodaj następujący wyróżniony kod znaczników, jeśli nie jest już istnieje:  
  
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
  
     Zakres zasobów jest określana przez gdy zdefiniujesz zasób. Definiowanie zasobów w `Application.Resources` w pliku app.xaml plik umożliwia zasobów do użycia w dowolnym miejscu w aplikacji. Aby dowiedzieć się więcej na temat definiowania zakresu zasobów, zobacz [zasoby XAML](../advanced/xaml-resources.md).  
  
2. **Tworzenie stylu i definiować wartości właściwości podstawowe z nią:** Dodaj następujący kod do `Application.Resources` bloku. Ten kod znaczników tworzy <xref:System.Windows.Style> która odnosi się do wszystkich przycisków w aplikacji, ustawienie <xref:System.Windows.FrameworkElement.Width%2A> przycisków do 90 i <xref:System.Windows.FrameworkElement.Margin%2A> 10:  
  
    ```xaml  
    <Application.Resources>  
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>  
    </Application.Resources>  
    ```  
  
     <xref:System.Windows.Style.TargetType%2A> Właściwość określa, że styl ma zastosowanie do wszystkich obiektów typu <xref:System.Windows.Controls.Button>. Każdy <xref:System.Windows.Setter> ustawienie wartości różnych właściwości <xref:System.Windows.Style>. W związku z tym w tym momencie każdy przycisk w aplikacji ma szerokość 90 i margines 10.  Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację, zobaczysz następujące okno.  
  
     ![Przyciski szerokość 90 i margines 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")  
  
     Jest znacznie więcej możliwości style, tym na różne sposoby, aby dostroić, które obiekty są stosowane, określając wartości właściwości złożonej i nawet przy użyciu stylów jako dane wejściowe dla innych stylów. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](styling-and-templating.md).  
  
3. **Ustaw wartość właściwości stylu do zasobu:** Zasoby Włącz prosty sposób na ponowne użycie typowych zdefiniowanych obiektów i wartości. Jest to szczególnie przydatne do definiowania złożonych wartości przy użyciu zasobów, aby sprawić, że kod jest bardziej moduły. Dodaj następujący wyróżniony kod znaczników do pliku app.xaml.  
  
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
  
     Bezpośrednio pod `Application.Resources` bloku, został utworzony zasób o nazwie "GrayBlueGradientBrush". Ten zasób definiuje gradient poziomy. Ten zasób może służyć jako wartość właściwości z dowolnego miejsca w aplikacji, między innymi wewnątrz metoda ustawiająca styl przycisku dla <xref:System.Windows.Controls.Control.Background%2A> właściwości. Teraz wszystkie przyciski powinny mieć <xref:System.Windows.Controls.Control.Background%2A> wartość właściwości to gradientu.  
  
     Naciśnij klawisz F5, aby uruchomić aplikację. Powinno to wyglądać następująco.  
  
     ![Przyciski z gradientu tła](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")  
  
## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Tworzenie szablonu, która definiuje wygląd przycisku  
 W tej sekcji utworzysz szablon, który dostosowuje wyglądu przycisku (prezentacja). Prezentacji przycisk składa się kilka obiektów, w tym prostokąty i inne składniki zapewniające niepowtarzalnego wyglądu przycisku.  
  
 Do tej pory kontroli wygląd przycisków w aplikacji ma została ograniczona do zmiana właściwości przycisku. Co zrobić, jeśli chcesz dokonać istotnych zmian wyglądu przycisku? Dzięki szablonom zaawansowane kontrolę nad prezentacji obiektu. Ponieważ szablony mogą być używane w ramach stylów, można zastosować szablonu do wszystkich obiektów, których dotyczy stylu (w tym przewodniku przycisk).  
  
#### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Aby użyć szablonu, aby zdefiniować wyglądu przycisku  
  
1. **Konfigurowanie szablonu:** Ponieważ kontrolki, takie jak <xref:System.Windows.Controls.Button> mają <xref:System.Windows.Controls.Control.Template%2A> właściwości, można zdefiniować wartości właściwości szablonu, podobnie jak inne wartości właściwości ustawimy w <xref:System.Windows.Style> przy użyciu <xref:System.Windows.Setter>. Dodaj następujący wyróżniony kod znaczników do własnego stylu przycisku.  
  
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
  
2. **Instrukcja ALTER prezentacji przycisku:** W tym momencie należy zdefiniować w szablonie. Dodaj następujący wyróżniony kod znaczników. Ten kod znaczników określa dwa <xref:System.Windows.Shapes.Rectangle> elementy z zaokrąglonymi narożnikami, następuje <xref:System.Windows.Controls.DockPanel>. <xref:System.Windows.Controls.DockPanel> Służy do hosta <xref:System.Windows.Controls.ContentPresenter> przycisku. A <xref:System.Windows.Controls.ContentPresenter> Wyświetla zawartość przycisku. W tym przewodniku zawartości jest tekst ("Przycisk 1", "Button 2", "Button 3"). Wszystkie składniki szablonu (prostokątów i <xref:System.Windows.Controls.DockPanel>) są ułożone wewnątrz <xref:System.Windows.Controls.Grid>.  
  
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
  
     Naciśnij klawisz F5, aby uruchomić aplikację. Powinno to wyglądać następująco.  
  
     ![](./media/custom-button-animatedbutton-4.gif "custom_button_AnimatedButton_4")  
  
3. **Dodaj glasseffect do szablonu:** Następnie dodasz szkła. Najpierw należy utworzyć niektóre zasoby tworzone efekt szkła gradientu. Dodaj zasobom gradientu w dowolnym miejscu w obrębie `Application.Resources` bloku:  
  
    ```xaml  
    <Application.Resources>  
      <GradientStopCollection x:Key="MyGlassGradientStopsResource">
        <GradientStop Color="WhiteSmoke" Offset="0.2" />     
        <GradientStop Color="Transparent" Offset="0.4" />    
        <GradientStop Color="WhiteSmoke" Offset="0.5" />     
        <GradientStop Color="Transparent" Offset="0.75" />     
        <GradientStop Color="WhiteSmoke" Offset="0.9" />     
        <GradientStop Color="Transparent" Offset="1" />   
      </GradientStopCollection>   
      <LinearGradientBrush x:Key="MyGlassBrushResource"    
        StartPoint="0,0" EndPoint="1,1" Opacity="0.75"
        GradientStops="{StaticResource MyGlassGradientStopsResource}" />  
    <!-- Styles and other resources below here. -->  
    ```  
  
     Te zasoby są używane jako <xref:System.Windows.Shapes.Shape.Fill%2A> dla prostokąt, który możemy wstawianie <xref:System.Windows.Controls.Grid> szablonu przycisku. Dodaj następujący wyróżniony kod znaczników do szablonu.  
  
    ```xaml
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
          <!-- These transforms have no effect as they are declared here.
          The reason the transforms are included is to be targets
          for animation (see later). -->       
          <Rectangle.RenderTransform>
            <TransformGroup>
              <ScaleTransform />
              <RotateTransform />
            </TransformGroup>
          </Rectangle.RenderTransform>
          <!-- A BevelBitmapEffect is applied to give the button a "Beveled" look. -->
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
    </ControlTemplate>  
    </Setter.Value>  
    ```  
  
     Należy zauważyć, że <xref:System.Windows.UIElement.Opacity%2A> prostokąta przy użyciu `x:Name` właściwość "glassCube" ma wartość 0, więc po uruchomieniu przykładu, nie ma prostokąt szkła nałożony na górze. Jest to spowodowane później dodamy Wyzwalacze w szablonie dla po użytkownik wchodzi w interakcję z przyciskiem. Jednak zobaczyć, jak przycisk wygląda teraz, zmieniając <xref:System.Windows.UIElement.Opacity%2A> wartości 1 i uruchamiania aplikacji. Zobacz poniższą ilustrację. Przed przejściem do następnego kroku, należy zmienić <xref:System.Windows.UIElement.Opacity%2A> na 0.  
  
     ![Przyciski niestandardowe, które zostały utworzone przy użyciu XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")  
  
## <a name="create-button-interactivity"></a>Tworzenie przycisku interakcyjność  
 W tej sekcji utworzysz wyzwalacze właściwości i wyzwalacze zdarzeń, aby zmienić wartości właściwości i uruchamianie animacji w odpowiedzi na akcje użytkownika, takie jak przesuwając wskaźnik myszy na przycisku, a następnie klikając polecenie.  
  
 Łatwe dodawanie interaktywności (myszą, pozostaw myszy, kliknij pozycję i tak dalej) jest zdefiniuj Wyzwalacze w stylu lub szablonu. Aby utworzyć <xref:System.Windows.Trigger>, takich jak zdefiniować właściwość "warunek": Przycisk <xref:System.Windows.UIElement.IsMouseOver%2A> wartość właściwości jest równa `true`. Następnie zdefiniuj metody ustawiające (Akcje), które mają miejsce, gdy spełniony jest warunek wyzwalacza.  
  
#### <a name="to-create-button-interactivity"></a>Aby utworzyć przycisk interakcyjność  
  
1. **Dodawanie wyzwalaczy szablonu:** Dodaj wyróżnione znaczników do szablonu.  
  
    ```xaml
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
  
2. **Dodaj wyzwalacze właściwości:** Dodaj wyróżnione znaczników `ControlTemplate.Triggers` bloku:  
  
    ```xaml
    <ControlTemplate.Triggers>  
  
      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>  
  
    <ControlTemplate.Triggers/>  
    ```  
  
     Naciśnij klawisz F5, aby uruchomić aplikację i zobaczyć efekt, podczas uruchamiania wskaźnik myszy nad przycisków.  
  
3. **Dodawanie wyzwalacza koncentracji uwagi:** Następnie dodamy kilka podobnych metod ustawiających, aby obsłużyć przypadek, gdy przycisk ma fokus (na przykład po kliknięciu przez użytkownika).  
  
    ```xaml  
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
  
     Naciśnij klawisz F5, aby uruchomić aplikację, a następnie kliknij jeden z przycisków. Zwróć uwagę, przycisk pozostaje wyróżniony, po kliknięciu ponieważ wciąż jest ustawiony fokus. Po kliknięciu przycisku inny przycisk Nowy przycisk uzyska fokus, gdy ostatnie traci go.  
  
4. **Dodawanie animacji do** <xref:System.Windows.UIElement.MouseEnter> **i** <xref:System.Windows.UIElement.MouseLeave> **:** Następnie dodamy niektórych animacji do wyzwalaczy. Dodaj następujący kod, dowolne miejsce wewnątrz elementu `ControlTemplate.Triggers` bloku.  
  
    ```xaml
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
  
     Prostokąt szkła zmniejszana, gdy wskaźnik myszy przesuwa się nad przyciskiem i zwraca z powrotem do normalnego rozmiaru po odsunięciu wskaźnika.  
  
     Istnieją dwa animacji, które są wyzwalane, gdy wskaźnik myszy nad przyciskiem (<xref:System.Windows.UIElement.MouseEnter> zdarzenie jest zgłaszane). Te animacji zmniejszyć prostokąt szkła wzdłuż osi X i Y. Zauważ, że właściwości na <xref:System.Windows.Media.Animation.DoubleAnimation> elementów — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Określa animacji ponad pół sekundy, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Określa, że szkła zmniejsza się o 10%.  
  
     Drugi wyzwalacz zdarzenia (<xref:System.Windows.UIElement.MouseLeave>) po prostu zatrzymuje pierwszy z nich. W chwili zatrzymania <xref:System.Windows.Media.Animation.Storyboard>, animowany właściwości powrócić do wartości domyślnych. W związku z tym kiedy użytkownik przesunie wskaźnik myszy poza przycisk, przycisk powraca do sposób, w jaki był, zanim wskaźnik myszy jest przesuwany nad przycisku. Aby uzyskać więcej informacji na temat animacji, zobacz [Przegląd animacja](../graphics-multimedia/animation-overview.md).  
  
5. **Dodawanie animacji do po kliknięciu przycisku:** Ostatnim krokiem jest dodać wyzwalacza, gdy użytkownik kliknie przycisk. Dodaj następujący kod, dowolne miejsce wewnątrz elementu `ControlTemplate.Triggers` bloku:  
  
    ```xaml
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
  
     Naciśnij klawisz F5, aby uruchomić aplikację i kliknij jeden z przycisków. Po kliknięciu przycisku, szkła prostokąt obraca się wokół.  
  
## <a name="summary"></a>Podsumowanie  
 W tym przewodniku wykonywane są następujące Ćwiczenia:  
  
- Docelowe <xref:System.Windows.Style> z typem obiektu (<xref:System.Windows.Controls.Button>).  
  
- Podstawowe właściwości przycisków w całej aplikacji, używając kontrolowane <xref:System.Windows.Style>.  
  
- Utworzone zasoby, takie jak gradientów do użycia dla wartości właściwości <xref:System.Windows.Style> metod ustawiających.  
  
- Dostosować wygląd przycisków w całej aplikacji, stosując szablon do przycisków.  
  
- Dostosowywać zachowanie dla przycisków w odpowiedzi na działanie użytkownika (takie jak <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave>, i <xref:System.Windows.Controls.Primitives.ButtonBase.Click>) które zawarte efektów animacji.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie przycisku przy użyciu programu Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Animacja — przegląd](../graphics-multimedia/animation-overview.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Efekty mapy bitowej — przegląd](../graphics-multimedia/bitmap-effects-overview.md)
