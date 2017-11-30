---
title: "Plik określony w nazwie pliku nie jest prawidłowym plikiem XML"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3275608a1871ac981eb5b3aa39f0be6ab4e758e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Plik określony w nazwie pliku nie jest prawidłowym plikiem XML
Nazwa pliku, który został dostarczony nie jest prawidłowym plikiem XML. Aby określić dozwolonych struktury i zawartości dokumentu XML, można użyć definicji typu dokumentu (DTD), schemat Microsoft XML-danych (XDR) lub schematu schematu XML definition language (XSD). Schematy XSD jest preferowany sposób, aby określić gramatyki XML w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  W niektórych wcześniejszych wersjach programu Visual Studio **Projektant XML** jest Projektant typizowane zbiory danych i schemat XML. **Projektant XML** nadal można tworzyć i edytować pliki schematów XML. Jednak w [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], Projektant tworzenia i edytowania typizowane zbiory danych **Projektant obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [tworzenie i edytowanie wpisanych zestawów danych](/visualstudio/data-tools/creating-and-editing-typed-datasets).  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź, czy są podawania poprawnej nazwy pliku.  
  
-   Sprawdź, czy określony plik zawiera prawidłowy kod XML przez ładowanie pliku XML, który chcesz sprawdzić do **Projektant XML**. Z **XML** menu, kliknij przycisk **zweryfikować XML**. Błędy są wyświetlane w **listy zadań**.  
  
-   Jeśli plik XML ma skojarzony schemat XML, sprawdź, czy elementy są widoczne w zdefiniowanej strukturze i że zawartość poszczególnych elementów zgodne typy zadeklarowane danych określonej w schemacie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml>  
 [Porady: analizowanie ścieżek pliku](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
