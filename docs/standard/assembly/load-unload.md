---
title: 'Instrukcje: ładowanie i zwalnianie zestawów'
description: Środowisko CLR automatycznie ładuje zestawy .NET, do których odwołuje się program. Można również dynamicznie ładować określone zestawy do domeny bieżącej aplikacji.
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: e6f1ede055dd3f68bced4eba527b2fc65f7d5715
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378682"
---
# <a name="how-to-load-and-unload-assemblies"></a>Instrukcje: ładowanie i zwalnianie zestawów
Zestawy, do których odwołuje się program, zostaną automatycznie załadowane przez środowisko uruchomieniowe języka wspólnego, ale możliwe jest również dynamiczne ładowanie określonych zestawów do domeny bieżącej aplikacji. Aby uzyskać więcej informacji, zobacz [instrukcje: ładowanie zestawów do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

W .NET Framework nie ma możliwości zwolnienia pojedynczego zestawu bez zwalniania wszystkich domen aplikacji, które go zawierają. Nawet jeśli zestaw wykracza poza zakres, rzeczywisty plik zestawu pozostanie załadowany do momentu, gdy wszystkie domeny aplikacji, które go zawierają, zostaną zwolnione. W programie .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> Klasa obsługuje zwalnianie zestawów. Aby uzyskać więcej informacji, zobacz [jak używać i debugować możliwość odciążania zestawów w programie .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>ładowanie i zwalnianie zestawów

Aby załadować zestaw do domeny aplikacji, należy użyć jednej z kilku metod obciążenia zawartych w klasach <xref:System.AppDomain> i <xref:System.Reflection.Assembly> . Aby uzyskać więcej informacji, zobacz [instrukcje: ładowanie zestawów do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Należy zauważyć, że platforma .NET Core obsługuje tylko jedną domenę aplikacji.

Aby zwolnić zestaw w .NET Framework, musisz zwolnić wszystkie domeny aplikacji, które go zawierają. Aby zwolnić domenę aplikacji, należy użyć <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).

Jeśli chcesz zwolnić niektóre zestawy, ale nie inne w aplikacji .NET Framework, rozważ utworzenie nowej domeny aplikacji, wykonanie kodu w tej domenie, a następnie zwolnienie tej domeny aplikacji. Aby uzyskać więcej informacji, zobacz [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](index.md)
- [Instrukcje: ładowanie zestawów do domeny aplikacji](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
