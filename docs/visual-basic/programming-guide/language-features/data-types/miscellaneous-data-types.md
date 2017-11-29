---
title: "Różne typy danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6bb86bb6d203aa4e6bdded27a4cb78a8155ddec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="miscellaneous-data-types-visual-basic"></a>Różne typy danych (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]udostępnia kilka typów danych, które nie są zorientowanych w kierunku cyfry lub znaki. Zamiast tego mają do czynienia specjalne dane takie jak tak/nie wartości, wartości daty/godziny i adresy obiektu.  
  
 Dla Tabela zawierająca porównanie side-by-side [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="boolean-type"></a>Typ Boolean  
 [— Typ danych logicznych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) jest wartość bez znaku, który jest interpretowany jako `True` lub `False`. Szerokość danych zależy od platformy implementującej. Jeśli zmienna może zawierać tylko dwa wartości, takie jak PRAWDA/FAŁSZ tak/nie lub Włącz/Wyłącz, Zadeklaruj ją jako `Boolean`.  
  
## <a name="date-type"></a>Date — typ  
 [Date — typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md) jest wartością 64-bitowego, która przechowuje informacje zarówno datę i godzinę. Jednostka reprezentuje 100 nanosekundach czas, który upłynął od początku (00:00:00) 1 stycznia 1 rok kalendarza gregoriańskiego. Jeśli zmienna może zawierać wartości daty i godziny, Zadeklaruj ją jako `Date`.  
  
## <a name="object-type"></a>Typ obiektu  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) jest 32-bitowy adres, który wskazuje na wystąpienie obiektu w aplikacji lub w innej aplikacji. `Object` Zmiennej może odwoływać się do dowolnego obiektu aplikacja rozpoznaje lub danych dowolnego typu danych. Dotyczy to zarówno *typów wartości*, takich jak `Integer`, `Boolean`i wystąpienia struktury i *typy referencyjne*, które są wystąpienia obiektów, takich jak utworzone na podstawie klasy `String`i <xref:System.Windows.Forms.Form>, a tablica wystąpień.  
  
 Jeśli zmienna przechowuje wskaźnik do wystąpienia klasy, która nie wiadomo, w czasie kompilacji lub dane różnych typów danych może wskazywać, Zadeklaruj ją jako `Object`.  
  
 Zaletą `Object` — typ danych jest, że można użyć go do przechowywania danych dowolnego typu danych. Wadą jest pociągnąć za sobą dodatkowe operacje zająć więcej czasu wykonywania i zwiększyć bezpieczeństwo aplikacji działać wolniej. Jeśli używasz `Object` ponieść zmiennej dla typów wartości, *boxing* i *rozpakowującej*. Jeśli używasz dla typów odwołań ponosisz *późne wiązanie*.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Podstawowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Numeryczne typy danych](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Znakowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Rozwiązywanie problemów z typów danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
