---
title: -Debug (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: 8bb2b411dc867b6a43e52058dccf2ac980cf0b1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922511"
---
# <a name="-debug-c-compiler-options"></a>-Debug (C# opcje kompilatora)
Opcja **-Debug** powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w pliku wyjściowym lub plikach.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Określenie `+`lub tylko **debugowanie**powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w bazie danych programu (plik. pdb). Określenie `-`, która obowiązuje, jeśli nie określono **-Debug**nie powoduje, że żadne informacje debugowania nie zostaną utworzone.  
  
 `full` &#124; `pdbonly`  
 Określa typ informacji o debugowaniu generowanych przez kompilator. Pełny argument, który obowiązuje, jeśli nie określono **-Debug: pdbonly**, umożliwia dołączenie debugera do uruchomionego programu. Określenie pdbonly umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla tylko asembler, gdy uruchomiony program zostanie dołączony do debugera.  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, aby utworzyć kompilacje debugowania. Jeśli nie określono polecenia **-Debug**, **-Debug +** lub **-Debug: Full** , nie będzie możliwe debugowanie pliku wyjściowego programu.  
  
 Jeśli używasz **-Debug: Full**, pamiętaj, że występuje pewien wpływ na szybkość i rozmiar kodu zoptymalizowanego pod kątem JIT oraz niewielki wpływ na jakość kodu z **-Debug: Full**. Zalecamy **debugowanie: pdbonly** lub brak pliku PDB do generowania kodu wydania.  
  
> [!NOTE]
> Jedna różnica między **debugowaniem: pdbonly** i **-Debug: Full** to the **-Debug: Full** kompilator emituje <xref:System.Diagnostics.DebuggableAttribute>, który jest używany do informowania kompilatora JIT, że dostępne są informacje debugowania. W związku z tym zostanie wyświetlony komunikat o błędzie, jeśli kod <xref:System.Diagnostics.DebuggableAttribute> zawiera wartość false, jeśli używasz **-Debug: Full**.  
  
 Aby uzyskać więcej informacji na temat konfigurowania wydajności debugowania aplikacji, zobacz [ułatwianie debugowania obrazu](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Aby zmienić lokalizację pliku. pdb, zobacz [-PDB (C# opcje kompilatora)](./pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Kliknij przycisk **Zaawansowane** .  
  
4. Zmodyfikuj właściwość **informacji o debugowaniu** .  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Umieść informacje o debugowaniu w `app.pdb`pliku wyjściowym:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
