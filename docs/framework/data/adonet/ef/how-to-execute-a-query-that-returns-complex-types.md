---
title: 'Instrukcje: Wykonywanie zapytania, które zwraca typy złożone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854642"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Instrukcje: Wykonywanie zapytania, które zwraca typy złożone
W tym temacie pokazano, jak wykonać [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytanie, które zwraca obiekty typu jednostki, które zawierają właściwość typu złożonego.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1. Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt tak, aby korzystał z Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Kliknij dwukrotnie plik. edmx, aby wyświetlić model w [oknie przeglądarki modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) Entity Designer. Na powierzchni Entity Designer wybierz `Email` właściwości `Contact` i `Phone` typu jednostki, a następnie kliknij prawym przyciskiem myszy i wybierz opcję **refaktoryzacji do nowego typu złożonego**.  
  
4. Nowy typ złożony z wybranymi `Email` i `Phone` właściwościami zostanie dodany do **przeglądarki modelu**. Typ złożony otrzymuje nazwę domyślną: Zmień nazwę typu na `EmailPhone` w oknie **Właściwości** . Ponadto nowa `ComplexProperty` właściwość jest dodawana `Contact` do typu jednostki. Zmień nazwę właściwości na`EmailPhoneComplexType.`  
  
     Informacje o tworzeniu i modyfikowaniu typów złożonych przy użyciu kreatora Entity Data Model można znaleźć w [temacie How to: Refaktoryzacja istniejących właściwości do właściwości](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) typu złożonego i [instrukcje: Tworzenie i modyfikowanie typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))złożonych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje zapytanie, `Contact` które zwraca kolekcję obiektów i wyświetla dwie właściwości `Contact` obiektów: `ContactID` oraz wartości `EmailPhoneComplexType` typu złożonego.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
