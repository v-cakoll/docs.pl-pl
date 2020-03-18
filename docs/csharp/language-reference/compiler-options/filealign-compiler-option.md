---
title: -filealign (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603009"
---
# <a name="-filealign-c-compiler-options"></a>-filealign (Opcje kompilatora C#)
Opcja **-filealign** umożliwia określenie rozmiaru sekcji w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Wartość określająca rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192. Wartości te znajdują się w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Każda sekcja zostanie wyrównana na granicy, która jest wielokrotnością wartości **-filealign.** Nie ma stałej wartości domyślnej. Jeśli **-filealign** nie jest określony, czas wykonywania języka wspólnego wybiera domyślne w czasie kompilacji.  
  
 Określając rozmiar sekcji, można mieć wpływ na rozmiar pliku wyjściowego. Modyfikowanie rozmiaru sekcji może być przydatne w przypadku programów, które będą uruchamiane na mniejszych urządzeniach.  
  
 Użyj [DUMPBIN,](/cpp/build/reference/dumpbin-options) aby wyświetlić informacje o sekcjach w pliku wyjściowym.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Kliknij przycisk **Zaawansowane.**  
  
4. Zmodyfikuj właściwość **Wyrównanie plików.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>kompilatora, zobacz .  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
