---
title: Podsumowanie procesu wnioskowania schematu elementu DataSet
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 35e9b67d2d0a47aa69eabdb4b7e94f95b0b9589f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833981"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Podsumowanie procesu wnioskowania schematu elementu DataSet
Proces wnioskowania najpierw określa, z dokumentu XML, które elementy zostaną wywnioskowane jako tabele. W pozostałej postaci kodu XML proces wnioskowania określa kolumny dla tych tabel. W przypadku tabel zagnieżdżonych proces wnioskowania generuje zagnieżdżone obiekty <xref:System.Data.DataRelation> i <xref:System.Data.ForeignKeyConstraint>.  
  
 Poniżej przedstawiono krótkie podsumowanie reguł wnioskowania:  
  
- Elementy, które mają atrybuty są wywnioskowane jako tabele.  
  
- Elementy, które mają elementy podrzędne są wywnioskowane jako tabele.  
  
- Elementy, które powtarzają się, są wywnioskowane jako jedna tabela.  
  
- Jeśli dokument lub element główny nie ma żadnych atrybutów i żadne elementy podrzędne, które zostałyby wywnioskowane jako kolumny, są wywnioskowane jako <xref:System.Data.DataSet>. W przeciwnym razie element dokumentu jest wywnioskowany jako tabela.  
  
- Atrybuty są wywnioskowane jako kolumny.  
  
- Elementy, które nie mają atrybutów ani elementów podrzędnych, i które nie powtarzają się, są wywnioskowane jako kolumny.  
  
- W przypadku elementów, które są wywnioskowane jako zagnieżdżone tabele w innych elementach, które są również wywnioskowane jako tabele, zagnieżdżona **relacja** między dwiema tabelami zostanie utworzona. Nowa kolumna klucza podstawowego o nazwie **TableName_Id** jest dodawana do obu tabel i używana przez **relację**. **Element ForeignKeyConstraint** jest tworzony między dwiema tabelami przy użyciu kolumny **TableName_Id** .  
  
- Dla elementów, które są wywnioskowane jako tabele i które zawierają tekst, ale nie zawierają elementów podrzędnych, dla tekstu każdego elementu jest tworzona nowa kolumna o nazwie **TableName_Text** . Jeśli element jest wywnioskowany jako tabela i zawiera tekst, ale również zawiera elementy podrzędne, tekst jest ignorowany.  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie relacyjnej struktury elementu DataSet z pliku XML](inferring-dataset-relational-structure-from-xml.md)
- [Ładowanie elementu DataSet z pliku XML](loading-a-dataset-from-xml.md)
- [Ładowanie informacji o schemacie elementu DataSet z pliku XML](loading-dataset-schema-information-from-xml.md)
- [Używanie języka XML w elemencie DataSet](using-xml-in-a-dataset.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
