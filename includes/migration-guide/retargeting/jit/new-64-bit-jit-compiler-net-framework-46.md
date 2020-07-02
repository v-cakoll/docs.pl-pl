---
ms.openlocfilehash: 0237c848d71150aaea1f9de4f4b16a0cbbc4ab3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615670"
---
### <a name="new-64-bit-jit-compiler-in-the-net-framework-46"></a>Nowy 64-bitowy kompilator JIT w .NET Framework 4,6

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,6, nowy, 64-bitowy kompilator JIT jest używany do kompilowania just in Time. W niektórych przypadkach zgłoszono nieoczekiwany wyjątek lub zaobserwowano inne zachowanie niż w przypadku, gdy aplikacja jest uruchamiana przy użyciu kompilatora 32-bitowego lub starszego, 64-bitowego kompilatora JIT. Ta zmiana nie ma wpływu na 32-bitowy kompilator JIT. Znane różnice obejmują następujące elementy:

- W pewnych warunkach operacja rozpakowywania może zgłosić <xref:System.NullReferenceException> kompilacje wydania z włączoną optymalizacją.
- W niektórych przypadkach wykonanie kodu produkcyjnego w dużej treści metody może spowodować wygenerowanie <xref:System.StackOverflowException> .
- W pewnych warunkach struktury przesłane do metody są traktowane jako typy referencyjne, a nie jako typy wartości w kompilacjach wydań. Jednym z manifestów tego problemu jest to, że poszczególne elementy w kolekcji pojawiają się w nieoczekiwanej kolejności.
- W pewnych warunkach porównanie <xref:System.UInt16> wartości z ich dużym zestawem bitowym jest nieprawidłowe, jeśli Optymalizacja jest włączona.
- W określonych warunkach, szczególnie podczas inicjowania wartości tablicowych, Inicjalizacja pamięci przez <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcję Il może inicjować pamięć z nieprawidłową wartością. Może to spowodować nieobsługiwany wyjątek lub nieprawidłowe dane wyjściowe.
- W niektórych rzadkich warunkach alternatywny test bitowy może zwrócić niepoprawną <xref:System.Boolean> wartość lub zgłosić wyjątek, jeśli Optymalizacja kompilatora jest włączona.
- W określonych warunkach, jeśli `if` instrukcja jest używana do testowania warunku przed wprowadzeniem `try` bloku i wyjścia z `try` bloku, a ten sam warunek jest obliczany w `catch` `finally` bloku lub, nowy 64-bitowy kompilator JIT usuwa `if` warunek z `catch` bloku lub, `finally` gdy optymalizuje kod. W związku z tym kod wewnątrz `if` instrukcji w `catch` `finally` bloku lub jest wykonywany bezwarunkowo.

#### <a name="suggestion"></a>Sugestia

**Eliminowanie znanych problemów** <br/> Jeśli napotkasz wymienione powyżej problemy, możesz je rozwiązać, wykonując jedną z następujących czynności:

- Uaktualnij do .NET Framework 4.6.2. Nowy kompilator 64-bitowy dołączony do .NET Framework 4.6.2 odnosi się do każdego z tych znanych problemów.
- Upewnij się, że wersja systemu Windows jest aktualna, uruchamiając Windows Update. Aktualizacje usługi dla .NET Framework 4,6 i 4.6.1 odnoszą się do każdego z tych problemów, z wyjątkiem w przypadku operacji rozpakowywania <xref:System.NullReferenceException> .
- Kompiluj ze starszym 64-bitowym kompilatorem JIT. Więcej informacji o tym, jak to zrobić, znajduje się w sekcji **eliminowanie innych problemów** .
**Eliminowanie innych problemów** <br/> Jeśli wystąpią inne różnice w zachowaniu kodu skompilowanego ze starszym kompilatorem 64-bitowym i nowym 64-bitowym kompilatorem JIT lub między wersjami Debug i Release aplikacji, które są kompilowane przy użyciu nowego, 64-bitowego kompilatora JIT, można wykonać następujące czynności w celu skompilowania aplikacji za pomocą starszego kompilatora 64-bitowego JIT :

- Dla poszczególnych aplikacji można dodać [<](~/docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element do pliku konfiguracji aplikacji. Następujące wyłączenie kompilacji z nowym 64-bitowym kompilatorem JIT, a zamiast tego używa starszego, 64-bitowego kompilatora JIT.

    ```xml
    <?xml version ="1.0"?>
    <configuration>
      <runtime>
       <useLegacyJit enabled="1" />
      </runtime>
    </configuration>
    ```

- Dla poszczególnych użytkowników można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość 1 powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość 0 powoduje wyłączenie i włączenie nowego kompilatora 64-bitowego JIT.
- Dla poszczególnych maszyn można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość `1` powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość `0` wyłącza ją i włącza nowy, 64-bitowy kompilator JIT.
Możesz również poinformować nas o problemie, zgłaszając usterkę w witrynie [Microsoft Connect](https://connect.microsoft.com/VisualStudio).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6         |
| Typ    | Przekierowanie |
