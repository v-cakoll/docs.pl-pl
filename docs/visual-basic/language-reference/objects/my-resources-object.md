---
title: "My.Resources — Obiekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords: My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b2a2de7229f59e7deea29fe4186a5e466459d9fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="myresources-object"></a>My.Resources — Obiekt
Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 `My.Resources` Obiektu zapewnia dostęp do zasobów aplikacji i pozwala dynamicznie pobrać zasobów dla aplikacji. Aby uzyskać więcej informacji, zobacz [zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources` Obiekt ujawnia tylko zasoby globalne. Nie ma dostępu do plików zasobów skojarzonych z formularzami. W formularzu musi uzyskiwać dostęp do zasobów formularza. Aby uzyskać więcej informacji, zobacz [wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Dostępne pliki specyficzne dla kultury zasobów aplikacji z `My.Resources` obiektu. Domyślnie `My.Resources` obiekt odwołuje się do zasobów z pliku zasobów zgodny kultury w <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> właściwości. Można jednak zmienić to zachowanie i określić określonej kultury dla zasobów. Aby uzyskać więcej informacji, zobacz [zasobów w aplikacjach pulpitu](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Właściwości  
 Właściwości `My.Resources` obiektu umożliwiają dostęp tylko do odczytu do zasobów aplikacji. Aby dodać lub usunąć zasoby, używać **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie zasobów](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Dostępne zasoby dodane za pośrednictwem **projektanta projektu** przy użyciu `My.Resources.``resourceName`.  
  
 Możesz również dodać lub usunąć pliki zasobów, zaznaczając projektu w **Eksploratora rozwiązań** i klikając **Dodaj nowy element** lub **Dodaj istniejący element** z  **Projekt** menu. Dostępne zasoby dodane w ten sposób za pomocą `My.Resources.``resourceFileName`.`resourceName`.  
  
 Każdy zasób ma nazwę, kategorii i wartość, a tych ustawień zasobu określenia sposobu wyświetlania właściwości dostępu do zasobu w `My.Resources` obiektu. Dla zasobów dodane w **projektanta projektu**:  
  
-   Nazwa właściwości, określa nazwę  
  
-   Dane zasobu są wartości właściwości,  
  
-   Kategoria określa typ właściwości:  
  
|Kategoria|Typ danych właściwości|  
|---|---|  
|**Ciągi**|[Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Obrazy**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> Pochodną klasy <xref:System.IO.Stream> klasy, więc można go użyć z metod, które przyjmują strumieni, takie jak <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> metody.|  
|**Pliki**|-   [Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md) w przypadku plików tekstowych.<br />-   <xref:System.Drawing.Bitmap>w przypadku plików obrazu.<br />-   <xref:System.Drawing.Icon>Ikona plików.<br />-   <xref:System.IO.UnmanagedMemoryStream>w przypadku plików dźwięku.|  
|**Inne**|Zależą od informacji w Projektancie **typu** kolumny.|  
  
## <a name="classes"></a>Klasy  
 `My.Resources` Obiekt udostępnia każdy plik zasobu jako klasa z właściwości udostępnionych. Nazwa klasy jest taka sama jak nazwa pliku zasobu. Zgodnie z opisem w poprzedniej sekcji, zasobów w pliku zasobów są widoczne jako właściwości w klasie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tytuł formularza zasobu ciągu o nazwie `Form1Title` w pliku zasobów aplikacji. Na przykład do pracy, aplikacja musi mieć ciągu o nazwie `Form1Title` w pliku zasobów. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie zasobów](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie ikonę w postaci ikony o nazwie `Form1Icon` jest przechowywana w pliku zasobów aplikacji. Na przykład do pracy, aplikacja musi mieć ikony o nazwie `Form1Icon` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie obraz tła formularza zasobu obrazu o nazwie `Form1Background`, która znajduje się w pliku zasobów aplikacji. W tym przykładzie działała, aplikacja musi mieć zasób obrazu o nazwie `Form1Background` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odtwarza dźwięk, który jest przechowywany jako audio zasób o nazwie `Form1Greeting` w pliku zasobów aplikacji. Na przykład do pracy, aplikacja musi mieć audio zasób o nazwie `Form1Greeting` w pliku zasobów. `My.Computer.Audio.Play` Metoda jest dostępna tylko dla aplikacji formularzy systemu Windows.  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pobierana wersja kultury francuski zasób ciągu aplikacji. Nosi nazwę zasobu `Message`. Aby zmienić kulturę który `My.Resources` używa obiektu, w przykładzie użyto <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 W tym przykładzie działała, aplikacja musi mieć ciągu o nazwie `Message` w jego zasobów plików i aplikacji powinny mieć wersję kultury francuski tego pliku zasobu Resources.fr FR.resx. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie zasobów](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Jeśli aplikacja nie ma wersji kultury francuski pliku zasobu `My.Resource` obiektu pobiera zasobu z pliku zasobu kultury domyślnej.  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie lub usuwanie zasobów](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)  
 [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet)  
 [Zasoby w aplikacjach klasycznych](../../../framework/resources/index.md)  
 [Wskazówki: Lokalizowanie formularzy systemu Windows](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)
