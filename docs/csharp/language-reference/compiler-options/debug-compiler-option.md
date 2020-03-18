---
title: -debug (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 8bb2b411dc867b6a43e52058dccf2ac980cf0b1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69922511"
---
# <a name="-debug-c-compiler-options"></a>-debug (Opcje kompilatora C#)
Opcja **-debug** powoduje, że kompilator generuje informacje debugowania i umieszcza je w pliku wyjściowym lub plikach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Określanie `+`lub po prostu **-debugowanie**powoduje, że kompilator generuje informacje debugowania i umieszcza je w bazie danych programu (plik pdb). Określenie `-`, które obowiązuje, jeśli nie określisz **-debug**, powoduje, że nie ma informacji debugowania, które mają być tworzone.  
  
 `full`&#124;`pdbonly`  
 Określa typ informacji debugowania generowanych przez kompilator. Pełny argument, który obowiązuje, jeśli nie określisz **-debug:pdbonly,** umożliwia dołączanie debugera do uruchomionego programu. Określanie pdbonly umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetli asembler tylko wtedy, gdy uruchomiony program jest dołączony do debugera.  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja służy do tworzenia kompilacji debugowania. Jeśli nie określono **-debug**, **-debug+** lub **-debug:full,** nie będzie można debugować pliku wyjściowego programu.  
  
 Jeśli używasz **-debug:full**, należy pamiętać, że istnieje pewien wpływ na szybkość i rozmiar kodu zoptymalizowanego jit i niewielki wpływ na jakość kodu z **-debug:full**. Zalecamy **-debug:pdbonly** lub brak PDB do generowania kodu wydania.  
  
> [!NOTE]
> Jedną z różnic między **-debug:pdbonly** i **-debug:full** jest to, że <xref:System.Diagnostics.DebuggableAttribute>z **-debug:full** kompilator emituje , który jest używany do informowania kompilatora JIT, że informacje debugowania są dostępne. W związku z tym pojawi się <xref:System.Diagnostics.DebuggableAttribute> błąd, jeśli kod zawiera zestaw false, jeśli używasz **-debug:full**.  
  
 Aby uzyskać więcej informacji na temat konfigurowania wydajności debugowania aplikacji, zobacz [Ułatwianie debugowania obrazu](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Aby zmienić lokalizację pliku pdb, zobacz [-pdb (Opcje kompilatora C#)](./pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Kliknij przycisk **Zaawansowane.**  
  
4. Zmodyfikuj **debugowanie** właściwości Info.  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Umieść informacje debugowania `app.pdb`w pliku wyjściowym:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
