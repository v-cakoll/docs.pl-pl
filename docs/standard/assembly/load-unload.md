---
title: 'Instrukcje: Ładowanie i zwalnianie zestawów'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973202"
---
# <a name="how-to-load-and-unload-assemblies"></a>Instrukcje: Ładowanie i zwalnianie zestawów
Zestawy, do których odwołuje się program, zostaną automatycznie załadowane przez środowisko uruchomieniowe języka wspólnego, ale możliwe jest również dynamiczne ładowanie określonych zestawów do domeny bieżącej aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikacji.

W .NET Framework nie ma możliwości zwolnienia pojedynczego zestawu bez zwalniania wszystkich domen aplikacji, które go zawierają. Nawet jeśli zestaw wykracza poza zakres, rzeczywisty plik zestawu pozostanie załadowany do momentu, gdy wszystkie domeny aplikacji, które go zawierają, zostaną zwolnione. W programie .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> Klasa obsługuje zwalnianie zestawów. Aby uzyskać więcej informacji, zobacz [jak używać i debugować możliwość odciążania zestawów w programie .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Ładowanie i zwalnianie zestawów

Aby załadować zestaw do domeny aplikacji, należy użyć jednej z kilku metod obciążenia zawartych w klasach <xref:System.AppDomain> i. <xref:System.Reflection.Assembly> Aby uzyskać więcej informacji, zobacz [jak: Ładowanie zestawów do domeny](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikacji. Należy zauważyć, że platforma .NET Core obsługuje tylko jedną domenę aplikacji. 

Aby zwolnić zestaw w .NET Framework, musisz zwolnić wszystkie domeny aplikacji, które go zawierają. Aby zwolnić domenę aplikacji, należy użyć <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz [jak: Zwolnij domenę](../../framework/app-domains/how-to-unload-an-application-domain.md)aplikacji.

Jeśli chcesz zwolnić niektóre zestawy, ale nie inne w aplikacji .NET Framework, rozważ utworzenie nowej domeny aplikacji, wykonanie kodu w tej domenie, a następnie zwolnienie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Zwolnij domenę](../../framework/app-domains/how-to-unload-an-application-domain.md)aplikacji.  

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](index.md)
- [Instrukcje: Ładowanie zestawów do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
