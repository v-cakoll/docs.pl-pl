---
title: "Niejawnie wpisane lambda — wyrażenia"
description: "Dowiedz się, dlaczego nie można zadeklarować wyrażenia lambda za pomocą deklaracji zmiennej typie określonym niejawnie."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 663613af001f9727c48bd48553540305e47a6bab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implicitly-typed-lambda-expressions"></a>Niejawnie wpisane lambda — wyrażenia

Nie używam `var` można zadeklarować tego drzewa wyrażenia. Niejawnie wpisane deklaracja zmiennej nie można użyć do zadeklarowania wyrażenia lambda.
Tworzy problem cykliczne logiki dla kompilatora. `var` Deklaracji informuje kompilator, aby ustalić typ zmiennej z typu wyrażenie po prawej stronie operatora przypisania. Wyrażenia lambda nie ma typu czasu kompilacji, ale jest możliwe do przekonwertowania na żadnych zgodnych delegata lub typ wyrażenia. Po przypisaniu wyrażenia lambda do zmiennej typu delegat lub wyrażenie nakazuje kompilatorowi i spróbuj przekonwertować wyrażenia lambda do delegata, który pasuje do podpisu "przypisane do" zmiennej lub wyrażenie. Kompilator musi spróbuj wprowadzić ten efekt na po prawej stronie przypisania zgodny typ po lewej stronie przypisania. 

Obie strony przypisania nie informuje kompilator, aby przyjrzeć się obiektu po drugiej stronie operatora przypisania i czy Moje typu zgodne.

Więcej informacji na Dlaczego języka C# określa tego zachowania, odczytując można uzyskać [w tym artykule](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Pobierz plik PDF)


