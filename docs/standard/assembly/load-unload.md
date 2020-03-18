---
title: 'Jak: Załadować i rozładować zespoły'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155779"
---
# <a name="how-to-load-and-unload-assemblies"></a>Jak: Załadować i rozładować zespoły
Zestawy, do których odwołuje się program, zostaną automatycznie załadowane przez czas wykonywania języka wspólnego, ale możliwe jest również dynamiczne ładowanie określonych zestawów do bieżącej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [Jak: Załadować zestawy do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

W platformie .NET Framework nie ma możliwości rozładowania pojedynczego zestawu bez zwalniania wszystkich domen aplikacji, które go zawierają. Nawet jeśli zestaw wykracza poza zakres, rzeczywisty plik zestawu pozostanie załadowany, dopóki wszystkie domeny aplikacji, które go zawierają, nie zostaną rozładowane. W .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> klasa obsługuje zwalnianie zestawów. Aby uzyskać więcej informacji, zobacz [Jak używać i debugować niezwalnialność zestawu w .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>ładowanie i zwalnianie zestawów

Aby załadować zestaw do domeny aplikacji, należy użyć jednej z <xref:System.AppDomain> <xref:System.Reflection.Assembly>kilku metod ładowania zawartych w klasach i . Aby uzyskać więcej informacji, zobacz [Jak: Załadować zestawy do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Należy zauważyć, że program .NET Core obsługuje tylko jedną domenę aplikacji.

Aby zwolnić zestawu w .NET Framework, należy zwolnić wszystkie domeny aplikacji, które go zawierają. Aby zwolnić domenę aplikacji, użyj tej <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz [Jak: Zwolnić domenę aplikacji](../../framework/app-domains/how-to-unload-an-application-domain.md).

Jeśli chcesz zwolnić niektóre zestawy, ale nie inne w aplikacji .NET Framework, rozważ utworzenie nowej domeny aplikacji, wykonanie kodu wewnątrz tej domeny, a następnie zwolnienie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [Jak: Zwolnić domenę aplikacji](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](index.md)
- [Jak: Załaduj zestawy do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
