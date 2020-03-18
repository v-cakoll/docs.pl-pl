---
title: -resource (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602525"
---
# <a name="-resource-c-compiler-options"></a>-resource (Opcje kompilatora C#)
Osadza określony zasób w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobów .NET Framework, który chcesz osadzić w pliku wyjściowym.  
  
 `identifier` (opcjonalnie)  
 Logiczna nazwa zasobu; nazwa, która jest używana do ładowania zasobu. Wartością domyślną jest nazwa nazwy pliku.  
  
 `accessibility-modifier` (opcjonalnie)  
 Dostępność zasobu: publiczna lub prywatna. Wartość domyślna jest publiczna.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [-linkresource,](./linkresource-compiler-option.md) aby połączyć zasób z zestawem i nie dodawać pliku zasobu do pliku wyjściowego.  
  
 Domyślnie zasoby są publiczne w zestawie, gdy są tworzone przy użyciu kompilatora C#. Aby zasoby były `private` prywatne, określ jako modyfikator ułatwień dostępu. Żadna inna `public` dostępność `private` nie jest lub jest dozwolona.  
  
 Jeśli `filename` jest plikiem zasobów .NET Framework utworzonym na przykład przez [resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku <xref:System.Resources> programistycznym, można uzyskać do niego dostęp za pomocą elementów członkowskich w obszarze nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Dla wszystkich innych zasobów `GetManifestResource` należy użyć <xref:System.Reflection.Assembly> metod w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 **-res** jest krótką formą **-resource**.  
  
 Kolejność zasobów w pliku wyjściowym jest określana na podstawie kolejności określonej w wierszu polecenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Dodaj plik zasobów do projektu.  
  
2. Wybierz plik, który chcesz osadzić w **Eksploratorze rozwiązań**.  
  
3. Wybierz **akcję kompilacji** dla pliku w oknie **Właściwości.**  
  
4. Ustaw **akcję kompilacji** na **osadzony zasób**.  
  
 Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.FileProperties2.BuildAction%2A>opcji kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Kompilowanie `in.cs` i dołączanie pliku `rf.resource`zasobów:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
