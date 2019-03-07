---
title: -subsystemversion — (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: 39b4fc82cce0916b34bffd0caa29f76223acf5d1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465456"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion — (Visual Basic)
Określa minimalną wersję podsystemu, na którym można uruchomić wygenerowany plik wykonywalny, określając w ten sposób wersje systemu Windows, na którym można uruchomić pliku wykonywalnego. Najczęściej ta opcja zapewnia, że plik wykonywalny mogą korzystać z funkcji zabezpieczeń, które nie są dostępne ze starszymi wersjami systemu Windows.  
  
> [!NOTE]
>  Aby określić samego podsystemu, użyj [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) — opcja kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
-subsystemversion:major.minor  
```  
  
## <a name="parameters"></a>Parametry  
 `major.minor`  
 Minimalna wymagana wersja podsystemu, wyrażone w notacji z kropką dla wersji głównych i pomocniczych. Na przykład można określić, że aplikacja nie może działać w system operacyjny starszy niż Windows 7 po ustawieniu wartości tej opcji na 6.01, zgodnie z opisem w tabeli w dalszej części tego tematu. Należy określić wartości dla `major` i `minor` jako liczby całkowite.  
  
 Wiodące wyzerowania `minor` wersji nie zmieniają wersji, ale czy końcowe zera. Na przykład 6.1 i 6.01 odwołują się do tej samej wersji, ale 6.10 odwołuje się do innej wersji. Zaleca się, wyrażanie wersję pomocniczą w postaci dwóch cyfr, aby uniknąć mylenia go.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono typowe wersji podsystemu Windows.  
  
|Wersja Windows|Wersję podsystemu|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>Wartości domyślne  
 Wartość domyślna **- subsystemversion** — opcja kompilatora jest zależna od warunki na poniższej liście:  
  
-   Wartość domyślna to 6.02, jeśli jest ustawiona na poniższej liście wszelkie — opcja kompilatora:  
  
    -   [-target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [-platform:arm](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   Wartość domyślna to 6.00, jeśli używasz programu MSBuild, gdy elementem docelowym [!INCLUDE[net_v45](~/includes/net-v45-md.md)], i nie został ustawiony opcji kompilatora, które zostały określone we wcześniejszej części tej listy.  
  
-   Wartość domyślna to 4.00, jeśli żaden z poprzednich warunków jest spełniony.  
  
## <a name="setting-this-option"></a>Ustawienie tej opcji  
 Aby ustawić **- subsystemversion** — opcja kompilatora w programie Visual Studio, należy otworzyć pliku .vbproj i określić wartość dla `SubsystemVersion` właściwość MSBuild XML. Nie można ustawić tę opcję w środowisku IDE programu Visual Studio. Aby uzyskać więcej informacji, zobacz "Wartości domyślnej" wcześniej w tym temacie lub [wspólne właściwości projektów MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).  
  

  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)

- [Właściwości programu MSBuild](/visualstudio/msbuild/msbuild-properties)
