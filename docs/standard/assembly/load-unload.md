---
title: 'Instrukcje: ładowanie i zwalnianie zestawów'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155779"
---
# <a name="how-to-load-and-unload-assemblies"></a>Instrukcje: ładowanie i zwalnianie zestawów
Zestawy, do których odwołuje się program, zostaną automatycznie załadowane przez środowisko uruchomieniowe języka wspólnego, ale możliwe jest również dynamiczne ładowanie określonych zestawów do domeny bieżącej aplikacji. Aby uzyskać więcej informacji, zobacz [instrukcje: ładowanie zestawów do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

W .NET Framework nie ma możliwości zwolnienia pojedynczego zestawu bez zwalniania wszystkich domen aplikacji, które go zawierają. Nawet jeśli zestaw wykracza poza zakres, rzeczywisty plik zestawu pozostanie załadowany do momentu, gdy wszystkie domeny aplikacji, które go zawierają, zostaną zwolnione. W programie .NET Core Klasa <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> obsługuje zwalnianie zestawów. Aby uzyskać więcej informacji, zobacz [jak używać i debugować możliwość odciążania zestawów w programie .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>ładowanie i zwalnianie zestawów

Aby załadować zestaw do domeny aplikacji, należy użyć jednej z kilku metod ładowania zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection.Assembly>. Aby uzyskać więcej informacji, zobacz [instrukcje: ładowanie zestawów do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Należy zauważyć, że platforma .NET Core obsługuje tylko jedną domenę aplikacji.

Aby zwolnić zestaw w .NET Framework, musisz zwolnić wszystkie domeny aplikacji, które go zawierają. Aby zwolnić domenę aplikacji, użyj metody <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).

Jeśli chcesz zwolnić niektóre zestawy, ale nie inne w aplikacji .NET Framework, rozważ utworzenie nowej domeny aplikacji, wykonanie kodu w tej domenie, a następnie zwolnienie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Zobacz też

- [C#Przewodnik programowania](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](index.md)
- [Instrukcje: ładowanie zestawów do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
