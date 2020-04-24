---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005597"
---
# <a name="-filealign"></a>-filealign
Określa, gdzie mają być wyrównane sekcje pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Wymagany. Wartość określająca wyrównanie sekcji w pliku wyjściowym. Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192. Te wartości są w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `-filealign` opcji, aby określić wyrównanie sekcji w pliku wyjściowym. Sekcje to bloki ciągłej pamięci w przenośnym pliku wykonywalnym (PE), który zawiera kod lub dane. `-filealign` Opcja umożliwia skompilowanie aplikacji z niestandardowym wyrównaniem; Większość deweloperów nie musi używać tej opcji.  
  
 Każda sekcja jest wyrównana na granicy, która jest wielokrotnością `-filealign` wartości. Nie ma żadnych stałych ustawień domyślnych. Jeśli `-filealign` nie jest określony, kompilator wybiera wartość domyślną w czasie kompilacji.  
  
 Określając rozmiar sekcji, można zmienić rozmiar pliku wyjściowego. Modyfikowanie rozmiaru sekcji może być przydatne w przypadku programów, które będą uruchamiane na mniejszych urządzeniach.  
  
> [!NOTE]
> `-filealign` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
