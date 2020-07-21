---
title: 'Środki zaradcze: nowy 64-bitowy kompilator JIT'
description: Zapoznaj się z nowym 64-bitowym kompilatorem JIT zawartym w .NET Framework 4,6 oraz nieoczekiwanym zachowaniem lub wyjątkami, które mogą wystąpić podczas kompilacji.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: f059cbdd3b2a66ac8a668b7b8a80d9ad1551fa64
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475232"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Środki zaradcze: nowy 64-bitowy kompilator JIT
Począwszy od .NET Framework 4,6, środowisko uruchomieniowe zawiera nowy, 64-bitowy kompilator JIT dla kompilacji just in Time. Ta zmiana nie ma wpływu na kompilację z 32-bitowym kompilatorem JIT.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Nieoczekiwane zachowanie lub wyjątki  
 W niektórych przypadkach kompilacja z nowym 64-bitowym kompilatorem JIT powoduje wyjątek czasu wykonywania lub zachowanie, które nie jest zaobserwowane podczas wykonywania kodu skompilowanego przez starszy, 64-bitowy kompilator JIT. Znane różnice obejmują następujące elementy:  
  
> [!IMPORTANT]
> Wszystkie znane problemy zostały rozwiązane w nowym kompilatorze 64-bitowym, który został wystawiony .NET Framework 4.6.2. Większość została również omówiona w wersjach usługi .NET Framework 4,6 i 4.6.1, które są dołączone do Windows Update. Te problemy można wyeliminować, upewniając się, że wersja systemu Windows jest aktualna, lub przez uaktualnienie do .NET Framework 4.6.2.  
  
- W pewnych warunkach operacja rozpakowywania może zgłosić <xref:System.NullReferenceException> kompilacje wydania z włączoną optymalizacją.  
  
- W niektórych przypadkach wykonanie kodu produkcyjnego w dużej treści metody może spowodować wygenerowanie <xref:System.StackOverflowException> .  
  
- W pewnych warunkach struktury przesłane do metody są traktowane jako typy referencyjne, a nie typy wartości w kompilacjach wydań. Jednym z manifestów tego problemu jest to, że poszczególne elementy w kolekcji pojawiają się w nieoczekiwanej kolejności.  
  
- W pewnych warunkach porównanie <xref:System.UInt16> wartości z ich dużym zestawem bitowym jest nieprawidłowe, jeśli Optymalizacja jest włączona.  
  
- W określonych warunkach, szczególnie podczas inicjowania wartości tablicowych, Inicjalizacja pamięci przez <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcję Il może inicjować pamięć z nieprawidłową wartością. Może to spowodować nieobsługiwany wyjątek lub nieprawidłowe dane wyjściowe.  
  
- W niektórych rzadkich warunkach alternatywny test bitowy może zwrócić niepoprawną <xref:System.Boolean> wartość lub zgłosić wyjątek, jeśli Optymalizacja kompilatora jest włączona.  
  
- W określonych warunkach, jeśli `if` instrukcja jest używana do testowania warunku przed wprowadzeniem `try` bloku i wyjścia z `try` bloku, a ten sam warunek jest obliczany w `catch` `finally` bloku lub, nowy 64-bitowy kompilator JIT usuwa `if` warunek z `catch` bloku lub, `finally` gdy optymalizuje kod. W związku z tym kod wewnątrz `if` instrukcji w `catch` `finally` bloku lub jest wykonywany bezwarunkowo.  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a>Eliminowanie znanych problemów  
 Jeśli napotkasz wymienione powyżej problemy, możesz je rozwiązać, wykonując jedną z następujących czynności:  
  
- Uaktualnij do .NET Framework 4.6.2. Nowy kompilator 64-bitowy dołączony do .NET Framework 4.6.2 odnosi się do każdego z tych znanych problemów.  
  
- Upewnij się, że wersja systemu Windows jest aktualna, uruchamiając Windows Update. Aktualizacje usługi dla .NET Framework 4,6 i 4.6.1 odnoszą się do każdego z tych problemów, z wyjątkiem w przypadku operacji rozpakowywania <xref:System.NullReferenceException> .  
  
- Kompiluj ze starszym 64-bitowym kompilatorem JIT. Więcej informacji o tym, jak to zrobić, znajduje się w sekcji [eliminowanie innych problemów](#Other) .  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a>Eliminowanie innych problemów  
 Jeśli wystąpią inne różnice w zachowaniu kodu skompilowanego ze starszym kompilatorem 64-bitowym i nowym 64-bitowym kompilatorem JIT lub między wersjami Debug i Release aplikacji, które są kompilowane przy użyciu nowego, 64-bitowego kompilatora JIT, można wykonać następujące czynności w celu skompilowania aplikacji za pomocą starszego kompilatora 64-bitowego JIT :  
  
- Dla poszczególnych aplikacji można dodać [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element do pliku konfiguracji aplikacji. Następujące wyłączenie kompilacji z nowym 64-bitowym kompilatorem JIT, a zamiast tego używa starszego, 64-bitowego kompilatora JIT.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Dla poszczególnych użytkowników można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość 1 powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość 0 powoduje wyłączenie i włączenie nowego kompilatora 64-bitowego JIT.  
  
- Dla poszczególnych maszyn można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość 1 powoduje włączenie starszego 64-bitowego kompilatora JIT; wartość 0 powoduje wyłączenie i włączenie nowego kompilatora 64-bitowego JIT.  
  
 Możesz również poinformować nas o problemie, zgłaszając usterkę w witrynie [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
- [\<useLegacyJit>Postaci](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
