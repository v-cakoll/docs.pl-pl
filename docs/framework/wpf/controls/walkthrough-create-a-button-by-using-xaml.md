---
title: 'Wskazówki: Tworzenie przycisku przy użyciu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
ms.assetid: 138c41c4-1759-4bbf-8d77-77031a06a8a0
ms.openlocfilehash: a8cc227703e81e5de9dea7e44e10dfecca2cd05c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646468"
---
# <a name="walkthrough-create-a-button-by-using-xaml"></a>Wskazówki: Tworzenie przycisku przy użyciu XAML

Celem tego przewodnika jest, aby dowiedzieć się, jak utworzyć przycisk animowany do użycia w aplikacji Windows Presentation Foundation (WPF). W tym instruktażu użyto stylów i szablonu do utworzenia dostosowanego zasobu przycisku, który umożliwia ponowne użycie kodu i oddzielenie logiki przycisku od deklaracji przycisków. Ten instruktaż jest napisany [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]w całości w .

> [!IMPORTANT]
> W tym przewodniku przedstawiono kroki tworzenia aplikacji przez wpisanie lub skopiowanie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i wklejenie do programu Visual Studio. Jeśli wolisz dowiedzieć się, jak utworzyć tę samą aplikację za pomocą [projektanta,](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)zobacz Tworzenie przycisku przy użyciu programu Microsoft Expression Blend .

Na poniższej ilustracji przedstawiono gotowe przyciski.

![Przyciski niestandardowe utworzone przy użyciu języka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-basic-buttons"></a>Tworzenie przycisków podstawowych

Zacznijmy od utworzenia nowego projektu i dodania kilku przycisków do okna.

### <a name="to-create-a-new-wpf-project-and-add-buttons-to-the-window"></a>Aby utworzyć nowy projekt WPF i dodać przyciski do okna

1. Uruchom program Visual Studio.

2. **Utwórz nowy projekt WPF:** W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**. Znajdź szablon **aplikacji systemu Windows (WPF)** i nazwij projekt "AnimatedButton". Spowoduje to utworzenie szkieletu dla aplikacji.

3. **Dodaj podstawowe przyciski domyślne:** Wszystkie pliki potrzebne do tego przewodnika są dostarczane przez szablon. Otwórz plik Window1.xaml, klikając go dwukrotnie w Eksploratorze rozwiązań. Domyślnie istnieje <xref:System.Windows.Controls.Grid> element w window1.xaml. Usuń <xref:System.Windows.Controls.Grid> element i dodaj kilka [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przycisków do strony, wpisując lub skopiując i wklejając następujący wyróżniony kod do pliku Window1.xaml:

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

     Naciśnij klawisz F5, aby uruchomić aplikację; powinien zostać wyświetlony zestaw przycisków, który wygląda jak na poniższym rysunku.

     ![Trzy podstawowe przyciski](./media/custom-button-animatedbutton-1.gif "custom_button_AnimatedButton_1")

     Po utworzeniu podstawowych przycisków zakończono pracę w pliku Window1.xaml. Pozostała część przewodnika koncentruje się na pliku app.xaml, definiując style i szablon przycisków.

## <a name="set-basic-properties"></a>Ustawianie podstawowych właściwości

Następnie ustawmy niektóre właściwości na tych przyciskach, aby kontrolować wygląd i układ przycisków. Zamiast ustawiać właściwości na przyciskach indywidualnie, można użyć zasobów do definiowania właściwości przycisku dla całej aplikacji. Zasoby aplikacji są koncepcyjnie podobne do zewnętrznych kaskadowych arkuszy stylów (CSS) dla stron sieci Web; jednak zasoby są znacznie bardziej wydajne niż kaskadowe arkusze stylów (CSS), jak widać pod koniec tego przewodnika. Aby dowiedzieć się więcej o zasobach, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

### <a name="to-use-styles-to-set-basic-properties-on-the-buttons"></a>Aby użyć stylów do ustawiania podstawowych właściwości przycisków

1. **Zdefiniuj blok Application.Resources:** Otwórz plik app.xaml i dodaj następujące wyróżnione znaczniki, jeśli jeszcze go tam nie ma:

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

     Zakres zasobu jest określany przez miejsce definiowania zasobu. Definiowanie zasobów `Application.Resources` w pliku app.xaml umożliwia użycie zasobu z dowolnego miejsca w aplikacji. Aby dowiedzieć się więcej na temat definiowania zakresu zasobów, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

2. **Utwórz styl i zdefiniuj za nim podstawowe wartości właściwości:** Dodaj do bloku następujące `Application.Resources` znaczniki. Ten znacznik <xref:System.Windows.Style> tworzy, który ma zastosowanie do wszystkich <xref:System.Windows.FrameworkElement.Width%2A> przycisków w aplikacji, ustawienie <xref:System.Windows.FrameworkElement.Margin%2A> przycisków do 90 i do 10:

    ```xaml
    <Application.Resources>
      <Style TargetType="Button">
        <Setter Property="Width" Value="90" />
        <Setter Property="Margin" Value="10" />
      </Style>
    </Application.Resources>
    ```

     Właściwość <xref:System.Windows.Style.TargetType%2A> określa, że styl ma zastosowanie <xref:System.Windows.Controls.Button>do wszystkich obiektów typu . Każdy <xref:System.Windows.Setter> ustawia inną wartość <xref:System.Windows.Style>właściwości dla . W związku z tym w tym momencie każdy przycisk w aplikacji ma szerokość 90 i margines 10.  Jeśli naciśniesz klawisz F5, aby uruchomić aplikację, zostanie wyświetlenie następującego okna.

     ![Przyciski o szerokości 90 i marginesie 10](./media/custom-button-animatedbutton-2.gif "custom_button_AnimatedButton_2")

     Istnieje znacznie więcej można zrobić ze stylami, w tym wiele sposobów, aby dostosować, jakie obiekty są kierowane, określając złożone wartości właściwości, a nawet przy użyciu stylów jako dane wejściowe dla innych stylów. Aby uzyskać więcej informacji, zobacz [Stylowanie i tworzenie szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

3. **Ustaw wartość właściwości stylu na zasób:** Zasoby umożliwiają prosty sposób ponownego użycia powszechnie zdefiniowanych obiektów i wartości. Jest to szczególnie przydatne do definiowania złożonych wartości przy użyciu zasobów, aby kod bardziej modułowe. Dodaj następujące wyróżnione znaczniki do pliku app.xaml.

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

     Bezpośrednio pod `Application.Resources` blokiem utworzono zasób o nazwie "GrayBlueGradientBrush". Ten zasób definiuje gradient poziomy. Ten zasób może służyć jako wartość właściwości z dowolnego miejsca w <xref:System.Windows.Controls.Control.Background%2A> aplikacji, w tym wewnątrz ustawiacza stylów przycisków dla właściwości. Teraz wszystkie przyciski <xref:System.Windows.Controls.Control.Background%2A> mają wartość właściwości tego gradientu.

     Naciśnij klawisz F5, aby uruchomić aplikację. Powinno to wyglądać następująco.

     ![Przyciski z tłem gradientowym](./media/custom-button-animatedbutton-3.gif "custom_button_AnimatedButton_3")

## <a name="create-a-template-that-defines-the-look-of-the-button"></a>Tworzenie szablonu definiujące wygląd przycisku

W tej sekcji należy utworzyć szablon, który dostosowuje wygląd (prezentację) przycisku. Prezentacja przycisków składa się z kilku obiektów, w tym prostokątów i innych składników, aby nadać przyciskowi niepowtarzalny wygląd.

Do tej pory kontrola wyglądu przycisków w aplikacji ograniczała się do zmiany właściwości przycisku. Co zrobić, jeśli chcesz wprowadzić bardziej radykalne zmiany w wyglądzie przycisku? Szablony umożliwiają zaawansowana kontrola nad prezentacją obiektu. Ponieważ szablony mogą być używane w stylach, można zastosować szablon do wszystkich obiektów, które stosuje się do (w tym instruktażu, przycisk).

### <a name="to-use-the-template-to-define-the-look-of-the-button"></a>Aby zdefiniować wygląd przycisku za pomocą szablonu

1. **Skonfiguruj szablon:** Ponieważ <xref:System.Windows.Controls.Button> formanty <xref:System.Windows.Controls.Control.Template%2A> takie jak mają właściwość, można zdefiniować wartość właściwości <xref:System.Windows.Style> szablonu, podobnie jak inne wartości właściwości, które ustawiliśmy w pliku . <xref:System.Windows.Setter> Dodaj do swojego stylu styl przycisku następujące wyróżnione znaczniki.

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

2. **Prezentacja przycisku Zmień:** W tym momencie należy zdefiniować szablon. Dodaj następujące wyróżnione znaczniki. Ten znacznik określa <xref:System.Windows.Shapes.Rectangle> dwa elementy z zaokrąglonymi krawędziami, po których następuje . <xref:System.Windows.Controls.DockPanel> Jest <xref:System.Windows.Controls.DockPanel> używany do <xref:System.Windows.Controls.ContentPresenter> hostowania przycisku. A <xref:System.Windows.Controls.ContentPresenter> wyświetla zawartość przycisku. W tym instruktażu zawartość jest tekstem ("Button 1", "Button 2", "Button 3"). Wszystkie składniki szablonu (prostokąty <xref:System.Windows.Controls.DockPanel>i) są rozmieszczone wewnątrz <xref:System.Windows.Controls.Grid>.

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

     ![Okno z 3 przyciskami](./media/custom-button-animatedbutton-4.gif)

3. **Dodaj efekt szkła do szablonu:** Następnie dodasz szybę. Najpierw należy utworzyć pewne zasoby, które tworzą efekt gradientu szkła. Dodaj te zasoby gradientu w dowolnym miejscu w `Application.Resources` bloku:

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

     Zasoby te są <xref:System.Windows.Shapes.Shape.Fill%2A> używane jako dla prostokąta, <xref:System.Windows.Controls.Grid> który wstawiamy do szablonu przycisku. Dodaj do szablonu następujące wyróżnione znaczniki.

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

     Należy zauważyć, że <xref:System.Windows.UIElement.Opacity%2A> prostokąt z `x:Name` właściwością "glassCube" wynosi 0, więc po uruchomieniu próbki nie widać szklanego prostokąta nałożonego na wierzchu. Dzieje się tak, ponieważ później dodamy wyzwalacze do szablonu, gdy użytkownik wchodzi w interakcję z przyciskiem. Jednak można zobaczyć, jak przycisk wygląda teraz, zmieniając <xref:System.Windows.UIElement.Opacity%2A> wartość na 1 i uruchomienie aplikacji. Zobacz poniższą ilustrację. Przed przejściem do następnego <xref:System.Windows.UIElement.Opacity%2A> kroku zmień z powrotem na 0.

     ![Przyciski niestandardowe utworzone przy użyciu języka XAML](./media/custom-button-animatedbutton-5.gif "custom_button_AnimatedButton_5")

## <a name="create-button-interactivity"></a>Tworzenie interaktywności przycisków

W tej sekcji utworzysz wyzwalacze właściwości i wyzwalacze zdarzeń, aby zmienić wartości właściwości i uruchomić animacje w odpowiedzi na akcje użytkownika, takie jak przesuwanie wskaźnika myszy nad przyciskiem i klikanie.

Łatwym sposobem na dodanie interaktywności (najechanie myszą, pozostawienie myszy, kliknięcie itd.) jest zdefiniowanie wyzwalaczy w szablonie lub stylu. Aby utworzyć <xref:System.Windows.Trigger>, należy zdefiniować właściwość "warunek", takich jak: Wartość właściwości przycisku <xref:System.Windows.UIElement.IsMouseOver%2A> jest równa . `true` Następnie należy zdefiniować ustawiające (akcje), które mają miejsce, gdy warunek wyzwalacza jest spełniony.

### <a name="to-create-button-interactivity"></a>Aby utworzyć interaktywność przycisków

1. **Dodaj wyzwalacze szablonów:** Dodaj wyróżniony znacznik do szablonu.

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

2. **Dodaj wyzwalacze właściwości:** Dodaj wyróżnione znaczniki `ControlTemplate.Triggers` do bloku:

    ```xaml
    <ControlTemplate.Triggers>

      <!-- Set properties when mouse pointer is over the button. -->   <Trigger Property="IsMouseOver" Value="True">     <!-- Below are three property settings that occur when the           condition is met (user mouses over button).  -->     <!-- Change the color of the outer rectangle when user           mouses over it. -->     <Setter Property ="Rectangle.Stroke" TargetName="outerRectangle"       Value="{DynamicResource {x:Static SystemColors.HighlightBrushKey}}" />     <!-- Sets the glass opacity to 1, therefore, the           glass "appears" when user mouses over it. -->     <Setter Property="Rectangle.Opacity" Value="1" TargetName="glassCube" />     <!-- Makes the text slightly blurry as though you           were looking at it through blurry glass. -->     <Setter Property="ContentPresenter.BitmapEffect"        TargetName="myContentPresenter">       <Setter.Value>         <BlurBitmapEffect Radius="1" />       </Setter.Value>     </Setter>   </Trigger>

    <ControlTemplate.Triggers/>
    ```

     Naciśnij klawisz F5, aby uruchomić aplikację i zobaczyć efekt po uruchomieniu wskaźnika myszy nad przyciskami.

3. **Dodaj wyzwalacz fokusu:** Następnie dodamy kilka podobnych ustawiaczy do obsługi sprawy, gdy przycisk ma fokus (na przykład po kliknięciu go przez użytkownika).

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

     Naciśnij klawisz F5, aby uruchomić aplikację i kliknij jeden z przycisków. Zwróć uwagę, że przycisk pozostaje podświetlony po kliknięciu, ponieważ nadal ma fokus. Jeśli klikniesz inny przycisk, nowy przycisk zyska fokus, podczas gdy ostatni go traci.

4. **Dodaj animacje dla** <xref:System.Windows.UIElement.MouseEnter> **i** <xref:System.Windows.UIElement.MouseLeave> **:** Następnie dodajemy kilka animacji do wyzwalaczy.   Dodaj następujące znaczniki w `ControlTemplate.Triggers` dowolnym miejscu wewnątrz bloku.

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

     Prostokąt szkła zmniejsza się, gdy wskaźnik myszy przesuwa się nad przyciskiem i powraca do normalnego rozmiaru, gdy wskaźnik odchodzi.

     Istnieją dwie animacje, które są wyzwalane, gdy<xref:System.Windows.UIElement.MouseEnter> wskaźnik przechodzi przez przycisk (zdarzenie jest wywoływane). Animacje te zmniejszają szklany prostokąt wzdłuż osi X i Y. Zwróć uwagę na <xref:System.Windows.Media.Animation.DoubleAnimation> właściwości <xref:System.Windows.Media.Animation.Timeline.Duration%2A> elementów — i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. Określa, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> że animacja występuje ponad pół <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> sekundy i określa, że szkło zmniejsza się o 10%.

     Drugi wyzwalacz<xref:System.Windows.UIElement.MouseLeave>zdarzenia ( ) po prostu zatrzymuje pierwszy. Po zatrzymaniu <xref:System.Windows.Media.Animation.Storyboard>, wszystkie animowane właściwości powrócić do wartości domyślnych. W związku z tym gdy użytkownik przesunie wskaźnik poza przycisk, przycisk wraca do sposobu, w jaki był przed wskaźnik myszy przeniósł się na przycisk. Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).

5. **Dodaj animację po kliknięciu przycisku:** Ostatnim krokiem jest dodanie wyzwalacza, gdy użytkownik kliknie przycisk. Dodaj następujące znaczniki w `ControlTemplate.Triggers` dowolnym miejscu wewnątrz bloku:

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

     Naciśnij klawisz F5, aby uruchomić aplikację, a następnie kliknij jeden z przycisków. Po kliknięciu przycisku, prostokąt szkła obraca się wokół.

## <a name="summary"></a>Podsumowanie
 W tym instruktażu wykonano następujące ćwiczenia:

- Celowane <xref:System.Windows.Style> a do<xref:System.Windows.Controls.Button>typu obiektu ( ).

- Kontrolowane podstawowe właściwości przycisków w całej <xref:System.Windows.Style>aplikacji za pomocą .

- Utworzone zasoby, takie jak gradienty <xref:System.Windows.Style> do użycia dla wartości właściwości ustawianych.

- Dostosowano wygląd przycisków w całej aplikacji, stosując szablon do przycisków.

- Dostosowane zachowanie przycisków w odpowiedzi na akcje <xref:System.Windows.UIElement.MouseEnter> <xref:System.Windows.UIElement.MouseLeave>użytkownika <xref:System.Windows.Controls.Primitives.ButtonBase.Click>(takie jak , i ), które zawierały efekty animacji.

## <a name="see-also"></a>Zobacz też

- [Tworzenie przycisku przy użyciu programu Microsoft Expression Blend](walkthrough-create-a-button-by-using-microsoft-expression-blend.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Przegląd Animacja](../graphics-multimedia/animation-overview.md)
- [Przegląd Malowanie jednolitymi kolorami i gradientami](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Przegląd Efekty mapy bitowej](../graphics-multimedia/bitmap-effects-overview.md)
