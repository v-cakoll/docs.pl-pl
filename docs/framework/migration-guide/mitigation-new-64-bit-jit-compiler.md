---
title: 'Środki zaradcze: Nowy kompilator JIT 64-bitowych'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22c98e41624abc931bd03e4ddea09ed55d0d3f39
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648483"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Środki zaradcze: Nowy kompilator JIT 64-bitowych
Począwszy od programu .NET Framework 4.6, środowisko uruchomieniowe zawiera nowe 64-bitowego kompilatora JIT dla kompilacji just in time. Ta zmiana nie ma wpływu na kompilacji z 32-bitowego kompilatora JIT.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Wyjątki lub nieoczekiwane zachowanie  
 W niektórych przypadkach kompilacji za pomocą nowego 64-bitowy kompilator JIT powoduje wyjątek czasu wykonywania, lub zachowanie, które nie zostanie wykryty podczas wykonywania kodu skompilowanego przez starsze 64-bitowego kompilatora JIT. Znane różnice są następujące:  
  
> [!IMPORTANT]
>  Rozwiązano wszystkich tych znanych problemów występujących w kompilator 64-bitowego wydania przy użyciu platformy .NET Framework 4.6.2. Większość ma również problem ten został rozwiązany w wersjach usługi programu .NET Framework 4.6 i 4.6.1, które są dołączone do aktualizacji Windows. Aby wyeliminować te problemy, zapewniając danej wersji systemu Windows jest aktualny, lub po uaktualnieniu do programu .NET Framework 4.6.2.  
  
- W pewnych okolicznościach może zgłaszać operacja rozpakowania <xref:System.NullReferenceException> w kompilacjach wydania przy użyciu optymalizacji włączona.  
  
- W niektórych przypadkach może zgłaszać wykonywania kodu produkcyjnego w treści metody dużych <xref:System.StackOverflowException>.  
  
- Pod pewnymi warunkami struktury przekazany do metody są traktowane jako typy odwołań, a nie typy wartości w wersji kompilacji. Jednym z przejawy tego problemu jest to, czy poszczególnych elementów w kolekcji są wyświetlane w nieoczekiwanej kolejności.  
  
- W pewnych okolicznościach porównanie <xref:System.UInt16> wartości za pomocą ich zestaw wysokobitowych jest nieprawidłowy, gdy Optymalizacja jest włączona.  
  
- Pod pewnymi warunkami, szczególnie podczas inicjowania tablicy wartości, inicjowanie pamięci przez <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcja IL może zainicjować pamięci o nieprawidłowej wartości. Może to spowodować w nieobsługiwany wyjątek lub nieprawidłowych danych wyjściowych.  
  
- W pewnych okolicznościach rzadkich test warunkowy bit może zwracać nieprawidłowe <xref:System.Boolean> wartość lub zgłosić wyjątek, jeśli są włączone optymalizacje kompilatora.  
  
- Pod pewnymi warunkami Jeśli `if` instrukcja jest używane do testowania dla warunku przed wejściem `try` bloku i wyjścia z `try` bloku, a tym samym stanie, które jest obliczane w `catch` lub `finally` bloku, Nowa Usuwa 64-bitowy kompilator JIT `if` warunku z `catch` lub `finally` zablokować, jeśli optymalizuje kod. W rezultacie kod wewnątrz `if` instrukcji w `catch` lub `finally` bezwarunkowo wykonaniu bloku.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Ograniczenie znane problemy  
 Jeśli wystąpią problemy z wymienionych powyżej, można je rozwiązać, wykonując następujące czynności:  
  
- Uaktualnianie do programu .NET Framework 4.6.2. Kompilator 64-bitowych dołączone do programu .NET Framework 4.6.2 dotyczy każdego z tych znanych problemów.  
  
- Upewnij się, że Twoja wersja programu Windows bądź na bieżąco, uruchamiając Windows Update. Aktualizacje usług .NET Framework 4.6 i 4.6.1 dotyczą każdego z tych problemów, z wyjątkiem <xref:System.NullReferenceException> w operacja rozpakowania.  
  
- Kompiluj przy użyciu starszych 64-bitowego kompilatora JIT. Zobacz [ograniczenia inne problemy z](#Other) sekcji, aby uzyskać więcej informacji na temat sposobu wykonania tego zadania.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Ograniczenie inne problemy  
 Jeśli występują inne różnice w zachowaniu między kodu skompilowanego za pomocą starszego kompilatora 64-bitowych i nowe 64-bitowy kompilator JIT lub debug i release wersje aplikacji, które przy użyciu nowego 64-bitowy kompilator JIT są kompilowane, można wykonaj następujące czynności Aby skompilować aplikację przy użyciu starszych 64-bitowy kompilator JIT:  
  
- Na podstawie poszczególnych aplikacji można dodać [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element do pliku konfiguracji aplikacji. Następujące wyłącza kompilacji za pomocą nowego 64-bitowy kompilator JIT i zamiast tego używa starszej wersji 64-bitowego kompilatora JIT.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Na poszczególnych użytkowników, możesz dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość 1 umożliwia starszej wersji 64-bitowy kompilator JIT; wartość 0 wyłącza je i włącza nowe 64-bitowego kompilatora JIT.  
  
- Na poszczególnych komputerach, można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość 1 umożliwia starszej wersji 64-bitowy kompilator JIT; wartość 0 wyłącza je i włącza nowe 64-bitowego kompilatora JIT.  
  
 Możesz również dać nam znać o problemie przez raportowanie błędów na [witryny Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany środowiska uruchomieniowego](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [\<useLegacyJit> Element](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
