---
title: '@ (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: f342f26ee8abe29e6c5a1477469c8b7292cd702e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259811"
---
# <a name="-c-compiler-options"></a>@ (opcje kompilatora C#)
@ Pozwala opcji, należy określić plik, który zawiera opcje kompilatora i pliki kodu źródłowego do skompilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Plik, który zawiera listę opcji kompilatora lub pliki kodu źródłowego do skompilowania.  
  
## <a name="remarks"></a>Uwagi  
 Opcje kompilatora i pliki kodu źródłowego zostanie przetworzony przez kompilator tak, jakby były one określone w wierszu polecenia.  
  
 Aby określić więcej niż jeden plik odpowiedzi w kompilacji, należy określić wiele opcji pliku odpowiedzi. Na przykład:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 W odpowiedzi na plik, wiele opcji kompilatora i pliki kodu źródłowego może znajdować się w jednym wierszu. Specyfikacja opcji kompilatora pojedynczego musi znajdować się w jednym wierszu (nie może obejmować wiele wierszy). Pliki odpowiedzi może mieć komentarze, które zaczynają się od symbolu #.  
  
 Określenie opcji kompilatora z pliku odpowiedzi jest podobne do wystawiania tych poleceń w wierszu polecenia. Zobacz [tworzenie z wiersza polecenia](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Aby uzyskać więcej informacji.  
  
 Po ich napotkaniu, kompilator przetwarza opcje polecenia. W związku z tym argumenty wiersza polecenia można zastąpić opcje wymienione wcześniej w plikach odpowiedzi. Z drugiej strony Opcje w pliku odpowiedzi zastępują opcje wymienione wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.  
  
 C# zawiera pliku csc.rsp, który znajduje się w tym samym katalogu co plik csc.exe. Zobacz [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) więcej informacji na temat csc.rsp.  
  
 Nie można ustawić tę opcję kompilatora w środowisku programowania Visual Studio i nie można go zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono kilka wierszy z przykładowego pliku odpowiedzi:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
