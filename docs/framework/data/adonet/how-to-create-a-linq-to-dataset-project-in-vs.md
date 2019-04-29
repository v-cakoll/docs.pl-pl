---
title: Tworzenie projektu LINQ to DataSet w programie Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667053"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Instrukcje: Tworzenie projektu LINQ to DataSet w programie Visual Studio

Różne rodzaje projektów LINQ wymagają pewnych odwołania do zestawów i importowanych przestrzeni nazw (Visual Basic) lub [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy (C#). Minimalne wymagania dla programu LINQ to odwołanie do *System.Core.dll* i `using` dyrektywy dla <xref:System.Linq>.

Te wymagania są określane domyślnie, jeśli tworzysz nowy projekt C# console aplikacji w programie Visual Studio 2017. Jeśli aktualizujesz projekt z wcześniejszej wersji programu Visual Studio, trzeba ręcznie podać te odwołania dotyczące LINQ.

LINQ do zestawu danych wymaga dwóch dodatkowych odwołania do *System.Data.dll* i *System.Data.DataSetExtensions.dll*.

> [!NOTE]
> Jeśli kompilujesz z wiersza polecenia, należy ręcznie odwołujesz się dll związane z LINQ w *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.

## <a name="to-enable-linq-to-dataset-functionality"></a>Aby włączyć LINQ do funkcji zestawu danych

Wykonaj następujące kroki w celu włączenia zapytań LINQ do funkcji zestawu danych w istniejącym projekcie.

1. Dodaj odwołania do **System.Core**, **System.Data**, i **System.Data.DataSetExtensions**.

   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie**. W **Menadżer odwołań** okno dialogowe, wybierz opcję **System.Core**, **System.Data**, i **System.Data.DataSetExtensions**. Kliknij przycisk **OK**.

1. Dodaj [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy (lub [importuje instrukcji](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) w języku Visual Basic) dla **System.Data** i **System.Linq**.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. Opcjonalnie dodaj `using` — dyrektywa (lub `Imports` instrukcji) dla **System.Data.Common** lub **System.Data.SqlClient**, w zależności od sposobu łączenia z bazą danych.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ to DataSet](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
