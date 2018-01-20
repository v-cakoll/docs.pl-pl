---
title: "Porady: Tworzenie składnika LINQ to projektu DataSet w programie Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c749cdd56f0c964b84788b05470406234ef3eb0a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Porady: Tworzenie składnika LINQ to projektu DataSet w programie Visual Studio
Różne typy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projekt wymaga niektórych importowane przestrzenie nazw (Visual Basic) lub `using` dyrektywy (C#) i odwołań. Minimalna wymagana wartość to odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq>. Domyślnie te są dostarczane w przypadku utworzenia nowego [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] projektu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]również wymaga odwołania do System.Data.dll i System.Data.DataSetExtensions.dll i `Imports` (Visual Basic) lub `using` — dyrektywa (C#).  
  
 Jeśli uaktualniasz projektu ze starszej wersji programu Visual Studio, trzeba będzie ręcznie podać te odwołania dotyczące LINQ. Ponadto może być konieczne ręczne ustawienie projekt pod kątem .NET Framework w wersji 3.5.  
  
> [!NOTE]
>  Jeśli tworzysz z wiersza polecenia, ręcznie musi odwoływać LINQ związane z bibliotek DLL w `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.  
  
### <a name="to-target-the-net-framework-35"></a>Docelowy .NET Framework 3.5  
  
1.  W [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], Utwórz nowy projekt Visual Basic lub C#. Alternatywnie możesz otworzyć projekt Visual Basic lub C#, który został utworzony w programie Visual Studio 2005 i postępuj zgodnie z monitami, aby przekonwertować go na [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projektu.  
  
2.  Dla projektu C#, kliknij przycisk **projektu** menu, a następnie kliknij przycisk **właściwości**.  
  
    1.  W **aplikacji** strony właściwości, wybierz program .NET Framework 3.5 w **platformy docelowej** listy rozwijanej.  
  
3.  Dla projektu Visual Basic, kliknij przycisk **projektu** menu, a następnie kliknij przycisk **właściwości**.  
  
    1.  W **skompilować** strony właściwości, kliknij przycisk **zaawansowane opcje kompilacji** , a następnie wybierz .NET Framework 3.5 w **platformy docelowej (wszystkie konfiguracje)** listy rozwijanej.  
  
4.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**, kliknij przycisk **.NET** karcie, przewiń w dół do **System.Core**, kliknij go, a następnie kliknij przycisk  **OK**.  
  
5.  Dodaj `using` dyrektywy lub importowanych przestrzeni nazw dla <xref:System.Linq> do pliku kodu źródłowego lub projektu.  
  
     Aby uzyskać więcej informacji, zobacz [dyrektywa using](~/docs/csharp/language-reference/keywords/using-directive.md) lub [porady: Dodawanie lub usuwanie zaimportowane przestrzenie nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>Aby włączyć LINQ do DataSet funkcji  
  
1.  Jeśli to konieczne, wykonaj kroki opisane wcześniej w tym temacie, można dodać odwołania do System.Core.dll i `using` dyrektywy lub importowanych przestrzeni nazw dla System.Linq.  
  
2.  W języku C# lub Visual Basic, kliknij przycisk **projektu** menu, a następnie kliknij przycisk **Dodaj odwołanie**.  
  
3.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** karcie, jeśli nie znajduje się na górze. Przewiń w dół do **system.dane** i **System.Data.DataSetExtensions** i kliknij je. Kliknij przycisk **OK** przycisku.  
  
4.  Dodaj `using` dyrektywy lub importowanych przestrzeni nazw dla <xref:System.Data> do pliku kodu źródłowego lub projektu. Aby uzyskać więcej informacji, zobacz [dyrektywa using](~/docs/csharp/language-reference/keywords/using-directive.md) lub [porady: Dodawanie lub usuwanie zaimportowane przestrzenie nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
5.  Dodaj odwołanie do System.Data.DataSetExtensions.dll dla technologii LINQ do Dataset funkcji. Dodaj odwołanie do System.Data.dll, jeśli jeszcze nie istnieje.  
  
6.  Opcjonalnie dodaj `using` dyrektywy lub importowanych przestrzeni nazw dla `System.Data.Common` lub `System.Data.SqlClient`, w zależności od sposobu łączenia z bazą danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [Wprowadzenie do korzystania z LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
