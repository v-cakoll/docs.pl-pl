---
title: -debug (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 4828e1cdd8b830f10b134b613bc96e69490091fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338491"
---
# <a name="-debug-c-compiler-options"></a>-debug (opcje kompilatora C#)
**-Debug** opcji powoduje, że kompilator generuje informacje o debugowaniu i umieść go w pliku danych wyjściowych lub plików.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Określanie `+`, lub po prostu **-debug**, powoduje, że kompilator generuje informacje o debugowaniu i umieść go w bazie danych programu (plik .pdb). Określanie `-`, ponieważ jest aktywna, jeśli nie określisz **-debug**, powoduje, że żadne informacje debugowania do utworzenia.  
  
 `full` &#124; `pdbonly`  
 Określa typ informacji o debugowaniu generowanych przez kompilator. Pełne argumentu, który znajduje się w efektu, jeśli nie określisz **-debug: pdbonly**, umożliwia dołączanie debugera do uruchomionego programu. Określenie "pdbonly" pozwala kodu źródłowego, debugowanie, gdy program jest uruchomiony w debugerze, ale będą wyświetlane tylko asemblera, gdy uruchomiony program jest dołączony do debugera.  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, aby utworzyć kompilacji do debugowania. Jeśli **-debug**, **-debugowania +**, lub **-debug: full** nie zostanie określony, nie można debugować pliku danych wyjściowych programu.  
  
 Jeśli używasz **-debug: full**, należy pamiętać, że istnieje pewien wpływ na szybkość i rozmiar zoptymalizowany kod JIT i mały wpływ na jakość kodu za pomocą **-debug: full**. Firma Microsoft zaleca **-debug: pdbonly** lub nie pliku PDB podczas generowania wersji kodu.  
  
> [!NOTE]
>  Jedną różnicą między **-debug: pdbonly** i **— debug: full** , w przypadku **— debug: full** kompilator generuje <xref:System.Diagnostics.DebuggableAttribute>, który jest używany do informują kompilator JIT czy dostępne są informacje debugowania. W związku z tym, otrzymasz błąd, jeśli kod zawiera <xref:System.Diagnostics.DebuggableAttribute> ustawiona na wartość false, jeśli używasz **-debug: full**.  
  
 Aby uzyskać więcej informacji na temat konfigurowania wydajność debugowania aplikacji, zobacz [ułatwianie obrazu do debugowania](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Aby zmienić lokalizację pliku .pdb, zobacz [- pdb (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz projekt **właściwości** strony.  
  
2. Kliknij przycisk **kompilacji** stronę właściwości.  
  
3. Kliknij przycisk **zaawansowane** przycisku.  
  
4. Modyfikowanie **informacje o debugowaniu** właściwości.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Przykład  
 Umieść informacje o debugowaniu w pliku wyjściowym `app.pdb`:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
