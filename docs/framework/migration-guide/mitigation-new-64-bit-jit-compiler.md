---
title: 'Łagodzenie: Nowy 64-bitowy kompilator JIT'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 883aaf032bde632b08f965d3450cfbea4feb8e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181258"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Łagodzenie: Nowy 64-bitowy kompilator JIT
Począwszy od .NET Framework 4.6, środowisko wykonawcze zawiera nowy kompilator JIT 64-bitowy dla kompilacji just-in-time. Ta zmiana nie wpływa na kompilację za pomocą 32-bitowego kompilatora JIT.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Nieoczekiwane zachowanie lub wyjątki  
 W niektórych przypadkach kompilacja z nowym kompilatorem JIT 64-bitowego powoduje wyjątek środowiska uruchomieniowego lub zachowanie, które nie jest obserwowane podczas wykonywania kodu skompilowanego przez starszy kompilator JIT 64-bitowego. Znane różnice są następujące:  
  
> [!IMPORTANT]
> Wszystkie te znane problemy zostały rozwiązane w nowym kompilatorze 64-bitowym wydanym za pomocą programu .NET Framework 4.6.2. Większość z nich została również omówiona w wersjach usług .NET Framework 4.6 i 4.6.1, które są dołączone do witryny Windows Update. Można wyeliminować te problemy, upewniając się, że wersja systemu Windows jest aktualna lub uaktualniając ją do programu .NET Framework 4.6.2.  
  
- Pod pewnymi warunkami operacja rozpakowywania może zgłosić <xref:System.NullReferenceException> w wersji kompilacji z optymalizacji włączone.  
  
- W niektórych przypadkach wykonanie kodu produkcyjnego w <xref:System.StackOverflowException>treści dużej metody może spowodować rzut .  
  
- Pod pewnymi warunkami struktury przekazywane do metody są traktowane jako typy odwołań, a nie typy wartości w kompilacjach release. Jednym z przejawów tego problemu jest to, że poszczególne elementy w kolekcji pojawiają się w nieoczekiwanej kolejności.  
  
- W pewnych warunkach <xref:System.UInt16> porównanie wartości z ich zestawem bitów jest niepoprawne, jeśli optymalizacja jest włączona.  
  
- W pewnych warunkach, szczególnie podczas inicjowania <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> wartości tablicy, inicjowanie pamięci przez instrukcję IL może zainicjować pamięć z niepoprawną wartością. Może to spowodować nieobsługiwał wyjątek lub niepoprawne dane wyjściowe.  
  
- W pewnych rzadkich warunkach test bitowy <xref:System.Boolean> warunkowy może zwrócić niepoprawną wartość lub zgłosić wyjątek, jeśli włączone są optymalizacje kompilatora.  
  
- Pod `if` pewnymi warunkami, jeśli instrukcja jest używana do `try` testowania warunku `try` przed wprowadzeniem bloku i `catch` w `finally` wyjściu z bloku, a ten sam warunek `if` jest `catch` oceniany w lub bloku, nowy kompilator JIT 64-bitowy usuwa warunek z lub `finally` bloku, gdy optymalizuje kod. W rezultacie kod wewnątrz `if` instrukcji `catch` w `finally` lub bloku jest wykonywany bezwarunkowo.  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a>Łagodzenie znanych problemów  
 Jeśli napotkasz problemy wymienione powyżej, możesz je rozwiązać, wykonując dowolną z następujących czynności:  
  
- Uaktualnienie do programu .NET Framework 4.6.2. Nowy kompilator 64-bitowy dołączony do programu .NET Framework 4.6.2 rozwiązuje każdy z tych znanych problemów.  
  
- Upewnij się, że twoja wersja systemu Windows jest aktualna, uruchamiając usługę Windows Update. Aktualizacje usługi do .NET Framework 4.6 i 4.6.1 <xref:System.NullReferenceException> rozwiązać każdy z tych problemów, z wyjątkiem w operacji rozpakowywania.  
  
- Skompiluj ze starszym 64-bitowym kompilatorem JIT. Zobacz [łagodzenia innych problemów](#Other) sekcji, aby uzyskać więcej informacji na temat sposobu wykonania tej sprawy.  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a>Łagodzenie innych problemów  
 Jeśli wystąpi jakakolwiek inna różnica w zachowaniu między kodem skompilowanym ze starszym kompilatorem 64-bitowym a nowym 64-bitowym kompilatorem JIT lub między wersjami debugowania i wersji aplikacji, które są skompilowane z nowym 64-bitowym kompilatorem JIT, możesz wykonać następujące czynności: , aby skompilować aplikację ze starszym 64-bitowym kompilatorem JIT:  
  
- Na podstawie dla aplikacji można dodać [ \<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element do pliku konfiguracji aplikacji. Następujące wyłącza kompilacji z nowym kompilatorem JIT 64-bit i zamiast tego używa starszego kompilatora JIT 64-bit.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Na podstawie dla użytkownika można dodać `REG_DWORD` wartość `useLegacyJit` o `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` nazwie do klucza rejestru. Wartość 1 umożliwia starszy kompilator JIT 64-bitowy; wartość 0 wyłącza go i włącza nowy kompilator JIT 64-bitowy.  
  
- Na podstawie na komputerze można dodać `REG_DWORD` wartość `useLegacyJit` o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` nazwie do klucza rejestru. Wartość 1 umożliwia starszy kompilator JIT 64-bitowy; wartość 0 wyłącza go i włącza nowy kompilator JIT 64-bitowy.  
  
 Możesz również poinformować nas o problemie, zgłaszając błąd w [usłudze Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
- [\<useLegacyJit> Element](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
