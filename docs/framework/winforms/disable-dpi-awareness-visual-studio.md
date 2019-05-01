---
title: Wyłącz rozpoznawanie DPI w programie Visual Studio
description: W tym artykule omówiono ograniczenia Windows Forms Designer na monitorach HDPI oraz sposobu uruchamiania programu Visual Studio jako proces świadomości DPI.
ms.date: 04/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.custom: seoapril2019
ms.openlocfilehash: e52debea382033417afe0bd47f899af1666192bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967235"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Wyłącz rozpoznawanie DPI w programie Visual Studio

Program Visual Studio jest kropki na aplikację świadomą CAL (DPI), co oznacza automatycznie skaluje ekran. Jeśli aplikacja stwierdzający, że nie jest obsługującą ustawienia DPI, systemu operacyjnego można skalować aplikację jako mapę bitową. To zachowanie jest również nazywany wirtualizacji DPI. Aplikacji nadal sądzą, że działa on w 100%, skalowanie lub rozdzielczości 96 dpi.

W tym artykule omówiono ograniczenia Windows Forms Designer na monitorach HDPI oraz sposobu uruchamiania programu Visual Studio jako proces świadomości DPI.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Windows Forms Designer na monitorach HDPI

**Windows Forms Designer** w programie Visual Studio nie ma skalowanie pomocy technicznej. Powoduje to, że problemy z wyświetlaniem otwieraniu niektórych formularzy w **Windows Forms Designer** na dużej liczbie punktów na cal (HDPI) monitorów. Aby uzyskać przykłady formanty może okazać się nakładają się, jak pokazano na poniższej ilustracji:

![Windows Forms Designer w monitorze HDPI](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

Po otwarciu formularza w **Windows Forms Designer** w programie Visual Studio na monitorze HDPI programu Visual Studio Wyświetla żółty informacyjny paska w górnej części projektanta:

![Pasek informacyjny w programie Visual Studio, aby ponownie uruchomić w trybie świadomości DPI](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

Odczytuje komunikat **skalowanie na ekranie głównym jest ustawiona na 200% (192 dpi). Może to spowodować problemy z renderowaniem w oknie projektanta.**

> [!NOTE]
> Ten pasek informacyjny została wprowadzona w Visual Studio 2017 w wersji 15.8.

Jeśli nie działają w projektancie, a nie trzeba dostosować układ formularza, można zignorować pasek informacyjny i kontynuować pracę w edytorze kodu lub w innych typach projektantów. (Możesz również [wyłączyć powiadomienia](#disable-notifications) tak, aby pasek informacyjny nie w dalszym ciągu są wyświetlane.) Tylko **Windows Forms Designer** dotyczy problem. Jeśli musisz pracować w **Windows Forms Designer**, następna sekcja pomoże Ci [stwierdzenie](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Aby rozwiązać problem z wyświetlaniem

Istnieją trzy opcje, aby rozwiązać problem z wyświetlaniem:

1. [Uruchom program Visual Studio jako proces świadomości DPI](#restart-visual-studio-as-a-dpi-unaware-process)
2. [Należy dodać wpis rejestru](#add-a-registry-entry)
3. [Ustaw skalowanie ustawienie do 100%](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Uruchom program Visual Studio jako proces świadomości DPI

Możesz ponownie uruchomić program Visual Studio jako proces świadomości DPI, wybierając opcję na żółty pasek informacyjny. Jest to preferowany sposób rozwiązanie problemu.

Po uruchomieniu programu Visual Studio jako proces świadomości DPI są rozwiązywane problemy układu projektanta, ale czcionki mogą pojawić się rozmyty. Programu Visual Studio wyświetla inny komunikat informacyjny żółty, gdy jest uruchamiany jako proces świadomości DPI, informujący, że **Visual Studio jest uruchomiony jako proces świadomości DPI. Projektanci WPF i XAML mogą być wyświetlane nieprawidłowo.** Pasek informacyjny zawiera także opcję **ponowne uruchomienie programu Visual Studio jako obsługującą ustawienia DPI proces**.

> [!NOTE]
> - Jeśli było oddokowane okien narzędzi w programie Visual Studio, w przypadku wybrania opcji, aby ponownie uruchomić jako proces świadomości DPI, położenie tych okien narzędzi, mogą ulec zmianie.
> - Jeśli używasz profilu domyślnego języka Visual Basic lub jeśli masz **Zapisz nowe projekty po utworzeniu** opcja jest wyłączona w **narzędzia** > **opcje**  >  **Projekty i rozwiązania**, Visual Studio nie można ponownie otworzyć projekt, po jej ponownym uruchomieniu jako proces świadomości DPI. Jednak można otworzyć projektu, wybierając je w obszarze **pliku** > **niedawne projekty i rozwiązania**.

Ważne jest, aby ponownie program Visual Studio jako obsługującą ustawienia DPI proces po zakończeniu pracy w **Windows Forms Designer**. Gdy jest uruchomiona jako proces świadomości DPI, czcionki mogą wyglądać rozmyte i może zostać wyświetlony problemów w innych projektantów, takich jak **projektanta XAML**. Po zamknięciu i ponownym otwarciu Visual Studio, gdy jest uruchomiona w trybie świadomości DPI, zostanie on obsługującą ustawienia DPI ponownie. Możesz również kliknąć **ponowne uruchomienie programu Visual Studio jako obsługującą ustawienia DPI proces** opcja na pasku informacyjnym.

### <a name="add-a-registry-entry"></a>Należy dodać wpis rejestru

Visual Studio można oznaczyć jako świadomości DPI przez modyfikację rejestru. Otwórz **Edytora rejestru** i Dodaj wpis do **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** podklucz:

**Wpis**: W zależności od tego, czy używasz programu Visual Studio 2017 lub 2019 r należy użyć jednej z następujących wartości:

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Jeśli używasz wersji Professional lub Enterprise programu Visual Studio, należy zastąpić **społeczności** z **Professional** lub **Enterprise** we wpisie. Również zastąpić literę dysku, zgodnie z potrzebami.

**Typ**: REG_SZ

**Wartość**: DPIUNAWARE

> [!NOTE]
> Program Visual Studio pozostaje w trybie świadomości DPI, dopóki nie usuniesz wpisu rejestru.

### <a name="set-your-display-scaling-setting-to-100"></a>Ustaw skalowanie ustawienie do 100%

Aby ustawić ekranu skalowanie ustawienie do 100% w systemie Windows 10, wpisz **ustawienia wyświetlania** na pasku wyszukiwania, a następnie zaznacz zadań **Zmienianie ustawień wyświetlania**. W **ustawienia** oknie **Zmień rozmiar tekstu, aplikacji i innych elementów** do **100%**.

Ustawianie ekranu skalowanie do 100% może być niepożądane, może sprawić, że interfejs użytkownika zbyt mały, może być używany.

## <a name="disable-notifications"></a>Wyłącz powiadomienia

Możesz nie otrzymywać powiadomienia o rozdzielczości DPI skalowanie problemy w programie Visual Studio. Możesz chcieć wyłączyć powiadomienia, jeśli nie działają w projektancie, na przykład.

Aby wyłączyć powiadomienia, wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego. Następnie wybierz **Windows Forms Designer** > **ogólne**i ustaw **powiadomienia skalowania DPI** do **False**.

![Wartość DPI skalowanie opcji powiadomień w programie Visual Studio](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

Jeśli chcesz później ponownie włączyć powiadomienia skalowania, ustaw właściwość na **True**.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli przejście rozpoznawanie DPI nie działa zgodnie z oczekiwaniami w programie Visual Studio, sprawdź, czy masz `dpiAwareness` wartość w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image pliku wykonywania Options\devenv.exe**  podkluczy w Edytorze rejestru. Jeśli jest obecny, usuń wartość.

## <a name="see-also"></a>Zobacz także

- [Automatyczne skalowanie w formularzach Windows Forms](automatic-scaling-in-windows-forms.md)
