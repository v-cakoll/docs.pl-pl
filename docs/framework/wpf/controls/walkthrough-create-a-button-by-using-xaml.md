---
title: 'Przewodnik: Utwórz przyciska przy użyciu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: 3f85d7d454247694d084ac68780f830c4301b6c7
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332800"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Przewodnik: Utwórz przyciska przy użyciu XAML

Celem tego instruktażu jest nauczenie się, jak utworzyć animowany przycisk do użycia w aplikacji Windows Presentation Foundation (WPF). W tym instruktażu zastosowano style i szablon w celu utworzenia niestandardowego zasobu przycisku, który umożliwia ponowne użycie kodu i rozdzielenie logiki przycisku z deklaracji przycisku. Ten Instruktaż jest zapisywana w całości w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

> [!IMPORTANT]
> Ten przewodnik przeprowadzi Cię przez kroki tworzenia aplikacji przez wpisanie lub skopiowanie i wklejenie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do Microsoft Visual Studio. Jeśli wolisz dowiedzieć się, jak używać narzędzia do projektowania (Microsoft Expression Blend) do tworzenia tej samej aplikacji, zobacz [Tworzenie przycisku przy użyciu programu Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md).

Na poniższej ilustracji przedstawiono gotowe przyciski.

![Niestandardowe przyciski, które zostały utworzone przy użyciu custom_button_AnimatedButton_5 języka XAML](./media/custom-button-animatedbutton-5.gif "")

## <a name="create-basic-buttons"></a>Utwórz podstawowe przyciski

Zacznijmy od utworzenia nowego projektu i dodania do okna kilku przycisków.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Aby utworzyć nowy projekt WPF i dodać przyciski do okna

1. Uruchom program Visual Studio.

2. **Utwórz nowy projekt WPF:** W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**. Znajdź szablon **aplikacji systemu Windows (WPF)** i Nadaj projektowi nazwę "AnimatedButton". Spowoduje to utworzenie szkieletu dla aplikacji.

3. **Dodaj podstawowe przyciski domyślne:** Wszystkie pliki potrzebne do tego przewodnika są udostępniane przez szablon. Otwórz plik window1. XAML, klikając go dwukrotnie w Eksplorator rozwiązań. Domyślnie istnieje element <xref:System.Windows.Controls.Grid> w window1. XAML. Usuń element <xref:System.Windows.Controls.Grid> i Dodaj kilka przycisków do strony [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], wpisując lub kopiując i wklejając następujący wyróżniony kod do window1. XAML:

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

     Naciśnij klawisz F5, aby uruchomić aplikację. powinien pojawić się zestaw przycisków, które wyglądają jak na poniższej ilustracji.

     ![Trzy podstawowe przyciski](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Teraz, gdy utworzono podstawowe przyciski, zakończysz pracę w pliku window1. XAML. Pozostała część przewodnika koncentruje się na pliku App. XAML, definiowaniu stylów i szablonie przycisków.

## <a name="set-basic-properties"></a>Ustaw właściwości podstawowe

Następnie Skonfigurujmy niektóre właściwości na tych przyciskach, aby kontrolować wygląd i układ przycisku. Zamiast ustawiania właściwości na przyciskach indywidualnie, użyjesz zasobów do definiowania właściwości przycisku dla całej aplikacji. Zasoby aplikacji są koncepcyjnie podobne do zewnętrznych kaskadowe arkusze stylów (CSS) dla stron sieci Web; jednak zasoby są znacznie bardziej wydajne niż kaskadowe arkusze stylów (CSS), jak widać na końcu tego instruktażu. Aby dowiedzieć się więcej o zasobach, zobacz [zasoby XAML](../advanced/xaml-resources.md).

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Aby użyć stylów do ustawiania podstawowych właściwości na przyciskach

1. **Zdefiniuj blok Application. Resources:** Otwórz plik App. XAML i Dodaj następujące wyróżnione znaczniki, jeśli jeszcze tego nie zrobiono:

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

     Zakres zasobów jest określany na podstawie tego, gdzie definiujesz zasób. Zdefiniowanie zasobów w `Application.Resources` w pliku App. XAML umożliwia użycie zasobu z dowolnego miejsca w aplikacji. Aby dowiedzieć się więcej o definiowaniu zakresu zasobów, zobacz [zasoby XAML](../advanced/xaml-resources.md).

2. **Utwórz styl i Zdefiniuj dla niego podstawowe wartości właściwości:** Dodaj następujący znacznik do bloku `Application.Resources`. Ten znacznik tworzy <xref:System.Windows.Style>, który ma zastosowanie do wszystkich przycisków w aplikacji, ustawiając <xref:System.Windows.FrameworkElement.Width%2A> przycisków na 90 i <xref:System.Windows.FrameworkElement.Margin%2A> do 10:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     Właściwość <xref:System.Windows.Style.TargetType%2A> Określa, że styl dotyczy wszystkich obiektów typu <xref:System.Windows.Controls.Button>. Każda <xref:System.Windows.Setter> ustawia inną wartość właściwości dla <xref:System.Windows.Style>. W związku z tym, w tym momencie każdy przycisk w aplikacji ma szerokość 90 i margines 10.  Jeśli naciśniesz klawisz F5, aby uruchomić aplikację, zobaczysz następujące okno.

     ![Przyciski o szerokości 90 i marginesie 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     Istnieje dużo więcej możliwości z stylami, w tym różne sposoby dostosowania obiektów do celów, określania złożonych wartości właściwości, a nawet style jako dane wejściowe dla innych stylów. Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](styling-and-templating.md).

3. **Ustaw wartość właściwości styl na zasób:** Zasoby umożliwiają proste użycie często zdefiniowanych obiektów i wartości. Jest to szczególnie przydatne do definiowania złożonych wartości przy użyciu zasobów, aby kod był bardziej modularny. Dodaj następujące wyróżnione znaczniki do pliku App. XAML.

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

     Bezpośrednio w bloku `Application.Resources` został utworzony zasób o nazwie "GrayBlueGradientBrush". Ten zasób definiuje gradient poziomy. Tego zasobu można używać jako wartości właściwości z dowolnego miejsca w aplikacji, w tym do metody ustawiającej styl przycisku dla właściwości <xref:System.Windows.Controls.Control.Background%2A>. Teraz wszystkie przyciski mają wartość właściwości <xref:System.Windows.Controls.Control.Background%2A> tego gradientu.

     Naciśnij klawisz F5, aby uruchomić aplikację. Powinien wyglądać podobnie do poniższego.

     ![Przyciski z custom_button_AnimatedButton_3 tła gradientu](./media/custom-button-animatedbutton-3.gif "")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Utwórz szablon definiujący wygląd przycisku

W tej sekcji utworzysz szablon, który dostosowuje wygląd przycisku. Prezentacja przycisku składa się z kilku obiektów, w tym prostokątów i innych składników, aby nadać przyciskowi unikatowy wygląd.

Do tej pory kontrolka wyglądu przycisków w aplikacji została ograniczona do zmiany właściwości przycisku. Co zrobić, jeśli chcesz wprowadzić bardziej podstawowe zmiany wyglądu przycisku? Szablony umożliwiają zaawansowaną kontrolę nad prezentacją obiektu. Ponieważ szablony mogą być używane w ramach stylów, można zastosować szablon do wszystkich obiektów, do których odnosi się ten styl (w tym instruktażu przycisk).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Aby użyć szablonu do zdefiniowania wyglądu przycisku

1. **Skonfiguruj szablon:** Ponieważ formanty takie jak <xref:System.Windows.Controls.Button> mają właściwość <xref:System.Windows.Controls.Control.Template%2A>, można zdefiniować wartość właściwości szablonu, tak jak w przypadku innych wartości właściwości ustawionych w <xref:System.Windows.Style> przy użyciu <xref:System.Windows.Setter>. Dodaj następujący wyróżniony znacznik do stylu przycisku.

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

2. **Zmień prezentację przycisku:** W tym momencie należy zdefiniować szablon. Dodaj następujący wyróżniony znacznik. Ten znacznik określa dwa elementy <xref:System.Windows.Shapes.Rectangle> z zaokrąglonymi krawędziami, po których następuje <xref:System.Windows.Controls.DockPanel>. @No__t-0 jest używany do hostowania <xref:System.Windows.Controls.ContentPresenter> przycisku. @No__t-0 wyświetla zawartość przycisku. W tym instruktażu zawartość jest tekstem ("Button 1", "Button 2", "Button 3"). Wszystkie składniki szablonu (prostokąty i <xref:System.Windows.Controls.DockPanel>) są określone w <xref:System.Windows.Controls.Grid>.

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

     Naciśnij klawisz F5, aby uruchomić aplikację. Powinien wyglądać podobnie do poniższego.

     ![Okno z 3 przyciskami](./media/custom-button-animatedbutton-4.gif)

3. **Dodaj GlassEffect do szablonu:** Następnie dodasz szklaną. Najpierw należy utworzyć zasoby, które tworzą efekt gradientu szkła. Dodaj te zasoby gradientowe w dowolnym miejscu w bloku `Application.Resources`:

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

     Te zasoby są używane jako <xref:System.Windows.Shapes.Shape.Fill%2A> dla prostokąta, który został wstawiony do <xref:System.Windows.Controls.Grid> szablonu przycisku. Dodaj następujący wyróżniony znacznik do szablonu.

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

     Zauważ, że <xref:System.Windows.UIElement.Opacity%2A> prostokąta z właściwością `x:Name` elementu "glassCube" jest równa 0, więc po uruchomieniu przykładu nie widzisz prostokąta szklanego przełożonego w górnej części. Dzieje się tak dlatego, że później dodamy wyzwalacze do szablonu, gdy użytkownik będzie współdziałać z przyciskiem. Można jednak zobaczyć, jak wygląda przycisk teraz, zmieniając wartość <xref:System.Windows.UIElement.Opacity%2A> na 1 i uruchamiając aplikację. Zapoznaj się z poniższym rysunkiem. Przed przejściem do następnego kroku Zmień wartość <xref:System.Windows.UIElement.Opacity%2A> z powrotem na 0.

     ![Niestandardowe przyciski, które zostały utworzone przy użyciu custom_button_AnimatedButton_5 języka XAML](./media/custom-button-animatedbutton-5.gif "")

## <a name="create-button-interactivity"></a>Utwórz interaktywny przycisk

W tej sekcji utworzysz wyzwalacze właściwości i wyzwalacze zdarzeń, aby zmienić wartości właściwości i uruchamiać animacje w odpowiedzi na akcje użytkownika, takie jak przesuwanie wskaźnika myszy nad przyciskiem i klikanie.

Prosty sposób na dodanie interaktywności (przesuwanie myszą, wyjście myszy, kliknięcie itd.) polega na zdefiniowaniu wyzwalaczy w szablonie lub stylu. Aby utworzyć <xref:System.Windows.Trigger>, należy zdefiniować Właściwość "warunek", taką jak: Wartość właściwości <xref:System.Windows.UIElement.IsMouseOver%2A> przycisku jest równa `true`. Następnie definiuje się metody ustawiające (akcje), które mają miejsce, gdy warunek wyzwalacza ma wartość true.

### <a name="to-create-button-interactivity"></a>Aby utworzyć interaktywny przycisk

1. **Dodaj wyzwalacze szablonu:** Dodaj wyróżnione adiustacje do szablonu.

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

2. **Dodaj wyzwalacze właściwości:** Dodaj wyróżnione znaczniki do bloku `ControlTemplate.Triggers`:

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     Naciśnij klawisz F5, aby uruchomić aplikację i zobaczyć efekt podczas uruchamiania wskaźnika myszy nad przyciskami.

3. **Dodaj wyzwalacz fokusu:** Następnie dodamy kilka podobnych metod ustawiających, aby obsłużyć przypadek, gdy przycisk ma fokus (na przykład po kliknięciu przez użytkownika).

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

     Naciśnij klawisz F5, aby uruchomić aplikację, a następnie kliknij jeden z przycisków. Zauważ, że przycisk pozostaje wyróżniony po kliknięciu go, ponieważ nadal ma fokus. Jeśli klikniesz inny przycisk, nowy przycisk stanie się fokusem, a ostatni z nich utraci.

4. **Dodaj animacje dla**  <xref:System.Windows.UIElement.MouseEnter> **i** <xref:System.Windows.UIElement.MouseLeave> **:** Następnie dodamy kilka animacji do wyzwalaczy. Dodaj następujący znacznik w dowolnym miejscu w bloku `ControlTemplate.Triggers`.

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

     Prostokąt szklany zmniejsza się, gdy wskaźnik myszy przesuwa się nad przycisk i wraca do normalnego rozmiaru przy opuszczaniu wskaźnika.

     Istnieją dwie animacje wyzwalane, gdy wskaźnik myszy znajduje się nad przyciskiem (zostanie zgłoszone zdarzenie <xref:System.Windows.UIElement.MouseEnter>). Te animacje zmniejszają prostokąt szklany wzdłuż osi X i Y. Zwróć uwagę na właściwości elementów <xref:System.Windows.Media.Animation.DoubleAnimation> — <xref:System.Windows.Media.Animation.Timeline.Duration%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. @No__t-0 Określa, że animacja występuje w ciągu 10 sekund, a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> określa, że szkło zmniejszy się o 10%.

     Drugi wyzwalacz zdarzenia (<xref:System.Windows.UIElement.MouseLeave>) po prostu kończy pierwszy. Po zatrzymaniu <xref:System.Windows.Media.Animation.Storyboard> wszystkie animowane właściwości zwracają do ich wartości domyślnych. W związku z tym, gdy użytkownik przesuwa wskaźnik poza przycisk, po przesunięciu wskaźnika myszy nad przycisk przechodzi do końca. Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).

5. **Dodaj animację dla momentu kliknięcia przycisku:** Ostatnim krokiem jest dodanie wyzwalacza, gdy użytkownik kliknie przycisk. Dodaj następujące znaczniki w dowolnym miejscu w bloku `ControlTemplate.Triggers`:

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

     Naciśnij klawisz F5, aby uruchomić aplikację, a następnie kliknij jeden z przycisków. Po kliknięciu przycisku, prostokąt szklany obraca się wokół siebie.

## <a name="summary"></a>Podsumowanie
 W tym instruktażu wykonasz następujące ćwiczenia:

- Celem <xref:System.Windows.Style> do typu obiektu (<xref:System.Windows.Controls.Button>).

- Kontrolowane podstawowe właściwości przycisków w całej aplikacji przy użyciu <xref:System.Windows.Style>.

- Utworzone zasoby, takie jak gradienty, które mają być używane dla wartości właściwości metod ustawiających <xref:System.Windows.Style>.

- Dostosowany wygląd przycisków w całej aplikacji przez zastosowanie szablonu do przycisków.

- Dostosowane zachowanie przycisków w odpowiedzi na akcje użytkownika (takie jak <xref:System.Windows.UIElement.MouseEnter>, <xref:System.Windows.UIElement.MouseLeave> i <xref:System.Windows.Controls.Primitives.ButtonBase.Click>), które uwzględniają efekty animacji.

## <a name="see-also"></a>Zobacz także

- [Tworzenie przycisku przy użyciu programu Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Animacja — przegląd](../graphics-multimedia/animation-overview.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Efekty mapy bitowej — przegląd](../graphics-multimedia/bitmap-effects-overview.md)
