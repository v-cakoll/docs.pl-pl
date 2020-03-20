---
title: Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180947"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
Ważne jest, aby przetestować kompilacje wersji aplikacji platformy uniwersalnej systemu Windows na ich platformach docelowych, ponieważ konfiguracje debugowania i wydania są zupełnie inne. Domyślnie konfiguracja debugowania używa środowiska uruchomieniowego .NET Core do skompilowania aplikacji, ale konfiguracja wersji używa platformy .NET Native do skompilowania aplikacji z kodem macierzystym.  
  
> [!IMPORTANT]
> Aby uzyskać informacje na temat radzenia sobie z [missingmetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) wyjątki, które można napotkać podczas testowania wersji aplikacji, zobacz "Krok 4: Ręczne rozwiązywanie brakujących metadanych: w temacie [Wprowadzenie,](getting-started-with-net-native.md) a także [odbicie i .NET Natywne](reflection-and-net-native.md) i [runtime dyrektywy (rd.xml) Odwołanie do pliku konfiguracyjnego](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Debugowanie i wydawanie kompilacji  
 Gdy kompilacja debugowania jest wykonywana względem środowiska uruchomieniowego .NET Core, nie została skompilowana do kodu macierzystego. Dzięki temu wszystkie usługi zwykle dostarczane przez środowisko wykonawcze są dostępne dla aplikacji.  
  
 Z drugiej strony kompilacja wydania kompiluje do kodu macierzystego dla swoich platform docelowych, usuwa większość zależności w zewnętrznych środowiskach uruchomieniowych i bibliotekach i mocno optymalizuje kod pod kątem maksymalnej wydajności.  
  
 Podczas debugowania kompilacji wydania, które są kompilowane przy użyciu platformy .NET Native:  
  
- Aparat debugowania natywnego platformy .NET różni się od zwykłych narzędzi debugowania platformy .NET.  
  
- Rozmiar pliku wykonywalnego jest zmniejszany w miarę możliwości. Jednym ze sposobów, że .NET Native zmniejsza rozmiar pliku wykonywalnego jest znacznie przycinanie komunikatów wyjątków środowiska uruchomieniowego, temat omówione bardziej szczegółowo w sekcji [Komunikaty wyjątków środowiska wykonawczego.](#Messages)  
  
- Kod jest mocno zoptymalizowany. Oznacza to, że inline jest używany, gdy jest to możliwe. (Inlining przenosi kod z procedur zewnętrznych do procedury wywoływania).   Fakt, że .NET Native zapewnia wyspecjalizowane środowisko uruchomieniowe i implementuje agresywne inline wpływa na stos wywołań, który jest wyświetlany podczas debugowania.  Aby uzyskać więcej informacji, zobacz [runtime call stack](#CallStack) sekcji.  
  
> [!NOTE]
> Można kontrolować, czy kompilacje debugowania i wydania są kompilowane za pomocą łańcucha narzędzi natywnych platformy .NET, zaznaczając lub odznaczając pole **łańcucha narzędzi Kompilacja za pomocą narzędzia .NET Native.**   Należy jednak pamiętać, że Sklep Windows zawsze skompiluje wersję produkcyjną aplikacji z łańcuchem narzędzi natywnych dla platformy .NET.  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a>Komunikaty o wyjątkach środowiska uruchomieniowego  
 Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, .NET Native nie zawiera pełnego tekstu komunikatów wyjątków. W rezultacie wyjątki środowiska uruchomieniowego zgłaszane w kompilacjach wydania mogą nie wyświetlać pełnego tekstu komunikatów wyjątków. Zamiast tego tekst może składać się z podciągów wraz z linkiem do naśladowania, aby uzyskać więcej informacji. Na przykład informacje o wyjątku mogą być wyświetlane jako:  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Jeśli potrzebujesz komunikatu o pełnym wyjątku, uruchom zamiast tego kompilację debugowania. Na przykład poprzednie informacje o wyjątku z kompilacji wydania mogą być wyświetlane w następujący sposób w kompilacji debugowania:  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a>Stos wywołań środowiska uruchomieniowego  
 Ze względu na inline i innych optymalizacji stos wywołań wyświetlany przez aplikację skompilowaną przez łańcuch narzędzi natywnych platformy .NET może nie pomóc w jasnych identyfikowaniu ścieżki do wyjątku środowiska uruchomieniowego.  
  
 Aby uzyskać pełny stos, uruchom kompilację debugowania zamiast tego.  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie natywnych aplikacji systemu Windows .NET](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Wprowadzenie](getting-started-with-net-native.md)
