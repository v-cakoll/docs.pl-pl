---
title: Wyrażenia lambda niejawnie wpisane
description: Dowiedz się, dlaczego nie można używać deklaracji zmiennej niejawnie wpisany do deklarowania wyrażenia lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 9b798f40676afaad2075806d6dc512f279bc7065
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672084"
---
# <a name="implicitly-typed-lambda-expressions"></a>Wyrażenia lambda niejawnie wpisane

Niejawnie wpisane deklaracji zmiennych nie można użyć do deklarowania wyrażenia lambda.
Tworzy problem cykliczne logiki dla kompilatora. `var` Deklaracji informuje kompilator, aby ustalić typ zmiennej z typu wyrażeniem po prawej stronie operatora przypisania. Wyrażenie lambda nie ma typów w czasie kompilacji, ale jest konwertowany na wszystkie dopasowania delegata lub typ wyrażenia. Po przypisaniu do wyrażenia lambda do zmiennej na delegata lub typ wyrażenia nakazuje kompilatorowi i spróbuj przekonwertować wyrażenia lambda na wyrażenie lub delegata, która pasuje do oznaczenia "przypisane do" zmiennej. Kompilator będą musieli spróbować dokonuje się po prawej stronie przypisania dopasowanie typu po lewej stronie przypisania w kolejności. 

Obie strony przypisania nie informuje kompilator, aby obejrzeć obiektu po drugiej stronie operatora przypisania i sprawdzić, czy mój typ odpowiada.

Można uzyskać nawet więcej informacji na temat Dlaczego języka C# określa to zachowanie, czytając [w tym artykule](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Pobierz plik PDF)
