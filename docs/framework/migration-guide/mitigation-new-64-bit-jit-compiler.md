---
title: 'Środki zaradcze: nowy 64-bitowy kompilator JIT'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: cad61bd86080fc21f0a47ef92b1908d6e7588a23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126244"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Środki zaradcze: nowy 64-bitowy kompilator JIT
Począwszy od .NET Framework 4,6, środowisko uruchomieniowe zawiera nowy, 64-bitowy kompilator JIT dla kompilacji just in Time. Ta zmiana nie ma wpływu na kompilację z 32-bitowym kompilatorem JIT.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Nieoczekiwane zachowanie lub wyjątki  
 W niektórych przypadkach kompilacja z nowym 64-bitowym kompilatorem JIT powoduje wyjątek czasu wykonywania lub zachowanie, które nie jest zaobserwowane podczas wykonywania kodu skompilowanego przez starszy, 64-bitowy kompilator JIT. Znane różnice obejmują następujące elementy:  
  
> [!IMPORTANT]
> Wszystkie znane problemy zostały rozwiązane w nowym kompilatorze 64-bitowym, który został wystawiony .NET Framework 4.6.2. Większość została również omówiona w wersjach usługi .NET Framework 4,6 i 4.6.1, które są dołączone do Windows Update. Te problemy można wyeliminować, upewniając się, że wersja systemu Windows jest aktualna, lub przez uaktualnienie do .NET Framework 4.6.2.  
  
- W pewnych warunkach operacja rozpakowywania może zgłosić <xref:System.NullReferenceException> w kompilacjach wydania z włączoną optymalizacją.  
  
- W niektórych przypadkach wykonanie kodu produkcyjnego w dużej treści metody może spowodować wygenerowanie <xref:System.StackOverflowException>.  
  
- W pewnych warunkach struktury przesłane do metody są traktowane jako typy referencyjne, a nie typy wartości w kompilacjach wydań. Jednym z manifestów tego problemu jest to, że poszczególne elementy w kolekcji pojawiają się w nieoczekiwanej kolejności.  
  
- W pewnych warunkach porównanie wartości <xref:System.UInt16> z ich zestawem High bit jest niepoprawne, jeśli Optymalizacja jest włączona.  
  
- W pewnych warunkach, szczególnie podczas inicjowania wartości tablicowych, Inicjalizacja pamięci za pomocą instrukcji <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL może inicjować pamięć z nieprawidłową wartością. Może to spowodować nieobsługiwany wyjątek lub nieprawidłowe dane wyjściowe.  
  
- W niektórych rzadkich warunkach alternatywny test bitowy może zwrócić niepoprawną wartość <xref:System.Boolean> lub zgłosić wyjątek, jeśli Optymalizacja kompilatora jest włączona.  
  
- W pewnych warunkach, jeśli instrukcja `if` jest używana do testowania warunku przed wprowadzeniem bloku `try` i w wyjściu z bloku `try` i ten sam warunek jest obliczany w bloku `catch` lub `finally` Nowy kompilator 64-bitowy JIT usuwa warunek `if` z bloku `catch` lub `finally`, gdy optymalizuje kod. W efekcie kod wewnątrz instrukcji `if` w bloku `catch` lub `finally` jest wykonywany bezwarunkowo.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Eliminowanie znanych problemów  
 Jeśli napotkasz wymienione powyżej problemy, możesz je rozwiązać, wykonując jedną z następujących czynności:  
  
- Uaktualnij do .NET Framework 4.6.2. Nowy kompilator 64-bitowy dołączony do .NET Framework 4.6.2 odnosi się do każdego z tych znanych problemów.  
  
- Upewnij się, że wersja systemu Windows jest aktualna, uruchamiając Windows Update. Aktualizacje usługi dla .NET Framework 4,6 i 4.6.1 dotyczą każdego z tych problemów, z wyjątkiem <xref:System.NullReferenceException> w operacji rozpakowywania.  
  
- Kompiluj ze starszym 64-bitowym kompilatorem JIT. Więcej informacji o tym, jak to zrobić, znajduje się w sekcji [eliminowanie innych problemów](#Other) .  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Eliminowanie innych problemów  
 Jeśli wystąpią inne różnice w zachowaniu kodu skompilowanego ze starszym kompilatorem 64-bitowym i nowym 64-bitowym kompilatorem JIT lub między wersjami Debug i Release aplikacji, które są kompilowane przy użyciu nowego, 64-bitowego kompilatora JIT, można wykonać następujące czynności Aby skompilować aplikację ze starszym 64-bitowym kompilatorem JIT:  
  
- Dla poszczególnych aplikacji można dodać [\<useLegacyJit >](../configure-apps/file-schema/runtime/uselegacyjit-element.md) elementu do pliku konfiguracji aplikacji. Następujące wyłączenie kompilacji z nowym 64-bitowym kompilatorem JIT, a zamiast tego używa starszego, 64-bitowego kompilatora JIT.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Dla poszczególnych użytkowników można dodać wartość `REG_DWORD` o nazwie `useLegacyJit` do klucza `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` rejestru. Wartość 1 powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość 0 powoduje wyłączenie i włączenie nowego kompilatora 64-bitowego JIT.  
  
- Na poszczególnych maszynach można dodać wartość `REG_DWORD` o nazwie `useLegacyJit` do klucza `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` rejestru. Wartość 1 powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość 0 powoduje wyłączenie i włączenie nowego kompilatora 64-bitowego JIT.  
  
 Możesz również poinformować nas o problemie, zgłaszając usterkę w witrynie [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany środowiska uruchomieniowego](runtime-changes-in-the-net-framework-4-6.md)
- [\<element > useLegacyJit](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
