---
title: -filealign (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f00db0cfd191de060b67aee4618d99740cb81248
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-filealign-c-compiler-options"></a>-filealign (opcje kompilatora C#)
**- Filealign** pozwala określić rozmiar sekcji w pliku danych wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Wartość określająca rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to 512, 1024, 2048, 4096 do 8192. Te wartości są w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Każda sekcja będzie wyrównany na granicy, która jest wielokrotnością liczby **- filealign** wartość. Nie jest domyślnie stałym. Jeśli **- filealign** nie zostanie określony, środowisko uruchomieniowe języka wspólnego wybiera domyślny, w czasie kompilacji.  
  
 Określając rozmiar sekcji wpływa na rozmiar pliku wyjściowego. Modyfikowanie rozmiar sekcji mogą być przydatne dla programów uruchamianych na mniejsze urządzenia.  
  
 Użyj [DUMPBIN](/cpp/build/reference/dumpbin-options) Aby wyświetlić informacje o sekcji w pliku danych wyjściowych.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **wyrównanie pliku** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
