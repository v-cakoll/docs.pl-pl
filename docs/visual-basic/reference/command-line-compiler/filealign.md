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
ms.openlocfilehash: 2893c1760a856a7d736e9c03ba33d9771722b5b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929469"
---
# <a name="-filealign"></a>-filealign
Określa, gdzie mają być wyrównane sekcje pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Wymagany. Wartość określająca wyrównanie sekcji w pliku wyjściowym. Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192. Te wartości są w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `-filealign` opcji, aby określić wyrównanie sekcji w pliku wyjściowym. Sekcje to bloki ciągłej pamięci w przenośnym pliku wykonywalnym (PE), który zawiera kod lub dane. `-filealign` Opcja umożliwia skompilowanie aplikacji z niestandardowym wyrównaniem; większość deweloperów nie musi używać tej opcji.  
  
 Każda sekcja jest wyrównana na granicy, która jest wielokrotnością `-filealign` wartości. Nie ma żadnych stałych ustawień domyślnych. Jeśli `-filealign` nie jest określony, kompilator wybiera wartość domyślną w czasie kompilacji.  
  
 Określając rozmiar sekcji, można zmienić rozmiar pliku wyjściowego. Modyfikowanie rozmiaru sekcji może być przydatne w przypadku programów, które będą uruchamiane na mniejszych urządzeniach.  
  
> [!NOTE]
> `-filealign` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
