---
title: 'Instrukcje: Wykonywanie zapytania, które zwraca typy złożone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 6c063c9ef6bfde868c773d941ba2107dbaa9ee73
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827126"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Instrukcje: Wykonywanie zapytania, które zwraca typy złożone
W tym temacie przedstawiono sposób wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytanie, które zwraca jednostki typu obiektów, które zawierają właściwość typu złożonego.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1.  Dodaj [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2.  Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Kliknij dwukrotnie plik edmx, aby wyświetlić model w [okna przeglądarki modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) Projektant jednostki. Na powierzchni projektanta jednostki wybierz `Email` i `Phone` właściwości `Contact` typu jednostki, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **refaktoryzacji na nowy typ złożony**.  
  
4.  Nowy typ złożony z wybranym `Email` i `Phone` właściwości jest dodawany do **przeglądarka modeli**. Typ złożony jest nadawana nazwa domyślna: zmiana nazwy typu, który ma `EmailPhone` w **właściwości** okna. Ponadto nowy `ComplexProperty` właściwość została dodana do `Contact` typu jednostki. Zmień nazwę właściwości do `EmailPhoneComplexType.`  
  
     Aby uzyskać informacji na temat tworzenia i modyfikowania typów złożonych za pomocą Kreator modelu Entity Data Model, zobacz [jak: Refaktoryzuj istniejących właściwości do właściwości typu złożonego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) i [jak: Tworzenie i modyfikowanie typów złożonych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje zapytanie, które zwraca kolekcję `Contact` obiektów i zostaną wyświetlone dwie właściwości `Contact` obiektów: `ContactID` i wartości `EmailPhoneComplexType` typu złożonego.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
