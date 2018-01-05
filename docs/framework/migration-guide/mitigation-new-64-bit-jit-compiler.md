---
title: "Środki zaradcze: Nowy kompilator JIT 64-bitowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ea1f5a832e2db63590fe5cbc3425078e17d3825
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Środki zaradcze: Nowy kompilator JIT 64-bitowych
Począwszy od programu .NET Framework 4.6 środowiska uruchomieniowego zawiera nowe kompilatora JIT 64-bitowej w czasie kompilacji. Ta zmiana nie wpływa na kompilacja z kompilatorem JIT 32-bitowych.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Nieoczekiwane zachowanie i wyjątków  
 W niektórych przypadkach kompilacji przez kompilator JIT 64-bitowych wynikiem wyjątek czasu wykonywania lub zachowania, które nie jest przestrzegana podczas wykonywania kodu skompilowanego przez starszego kompilatora JIT 64-bitowych. Znane różnice są następujące:  
  
> [!IMPORTANT]
>  Wszystkie te znane problemy rozwiązano w kompilator 64-bitowych publikowana z programu .NET Framework 4.6.2. Większość rozwiązano także w wersjach usługi .NET Framework 4.6 i 4.6.1, które są dołączone do usługi Windows Update. Można wyeliminować te problemy przez zapewnienie im, które danej wersji systemu Windows jest aktualny, albo przez uaktualnienie programu .NET Framework 4.6.2.  
  
-   W niektórych warunkach może zgłaszać rozpakowującej operacji <xref:System.NullReferenceException> w kompilacjach wydania z optymalizacją włączona.  
  
-   W niektórych przypadkach może zgłaszać wykonywanie kodu produkcyjnego w treści metody dużych <xref:System.StackOverflowException>.  
  
-   W niektórych warunkach struktury przekazana do metody są traktowane jako typów referencyjnych zamiast typów wartości w wersji kompilacji. Jednym z przejawy tego problemu jest czy poszczególnych elementów w kolekcji są wyświetlane w kolejności nieoczekiwany.  
  
-   W niektórych warunkach porównanie <xref:System.UInt16> wartości z ich wysokobitowe zestawu jest nieprawidłowa, gdy Optymalizacja jest włączona.  
  
-   W niektórych warunkach, szczególnie gdy inicjowanie tablicy wartości, inicjowania pamięci przez <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcji IL może zainicjować pamięci z niepoprawną wartość. Dzięki temu można w nieobsługiwany wyjątek lub nieprawidłowych danych wyjściowych.  
  
-   W niektórych warunkach rzadkich test warunkowy bit może zwrócić nieprawidłowym <xref:System.Boolean> wartość lub zgłosić wyjątek, jeśli jest włączona Optymalizacja kompilatora.  
  
-   W niektórych warunkach Jeśli `if` testować warunek przed wprowadzeniem używana jest instrukcja `try` bloku i wyjście z `try` bloku, a tym samym stanie, które są oceniane w `catch` lub `finally` bloku, nowy Kompilator JIT 64-bitowy usuwa `if` warunku z `catch` lub `finally` zablokować, jeśli optymalizuje kod. W związku z tym kodu wewnątrz `if` instrukcji w `catch` lub `finally` bezwarunkowo wykonaniu bloku.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Ograniczenie znane problemy  
 Jeśli wystąpią problemy z wymienionych powyżej, można rozwiązać je, wykonując jedną z następujących czynności:  
  
-   Uaktualnianie do programu .NET Framework 4.6.2. Kompilator 64-bitowych uwzględnionych w programie .NET Framework 4.6.2 adresów każdego z tych znanych problemów.  
  
-   Upewnij się, że danej wersji systemu Windows jest aktualny, uruchamiając usługi Windows Update. Usługi aktualizacji programu .NET Framework 4.6 i 4.6.1 dotyczą każdego z tych problemów, z wyjątkiem <xref:System.NullReferenceException> w rozpakowującej operacji.  
  
-   Kompiluj z użyciem starszego kompilatora JIT 64-bitowych. Zobacz [ograniczenie inne problemy](#Other) sekcji, aby uzyskać więcej informacji na temat sposobu wykonania tego zadania.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Ograniczenie inne problemy  
 Jeśli występują inne różnice w zachowaniu między kodu skompilowanego za pomocą starszego kompilatora 64-bitowe i kompilator JIT 64-bitowych lub debug i release wersje aplikacji, które przez kompilator JIT 64-bitowych są kompilowane, można wykonaj następujące czynności do kompilowania aplikacji za pomocą starszego kompilatora JIT 64-bitowe:  
  
-   Na poszczególnych aplikacji, co można dodać [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) elementu do pliku konfiguracji aplikacji. Następujące wyłącza kompilacji przez kompilator JIT 64-bitowe i zamiast tego używa starszej wersji kompilatora JIT 64-bitowych.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   Na podstawie użytkownika, można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość 1 powoduje włączenie starszej wersji 64-bitowej przy użyciu kompilatora JIT; wartość 0 powoduje wyłączenie go i włącza kompilator JIT 64-bitowych.  
  
-   Na poszczególnych komputerach, można dodać `REG_DWORD` wartość o nazwie `useLegacyJit` do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza rejestru. Wartość 1 powoduje włączenie starszej wersji 64-bitowej przy użyciu kompilatora JIT; wartość 0 powoduje wyłączenie go i włącza kompilator JIT 64-bitowych.  
  
 Można również Daj nam wiedzę na temat problemu przez raportowanie błędów na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany środowiska uruchomieniowego](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 [\<useLegacyJit > — Element](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
