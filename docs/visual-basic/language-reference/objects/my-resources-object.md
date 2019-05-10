---
title: My.resources — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 02e29b17404da0e868973364b0b17b5c4ca418c6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647628"
---
# <a name="myresources-object"></a>My.Resources — Obiekt
Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 `My.Resources` Obiekt zapewnia dostęp do zasobów aplikacji i umożliwia dynamicznie pobrać zasobów dla aplikacji. Aby uzyskać więcej informacji, zobacz [zasobów zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources` Obiekt udostępnia tylko zasoby globalne. Zapewnia ona dostęp do plików zasobów skojarzonych z formularzami. Należy uzyskać dostęp do zasobów formularza z formularza.  
  
 Możesz uzyskać dostęp pliki specyficzne dla kultury zasobów aplikacji z `My.Resources` obiektu. Domyślnie `My.Resources` obiekt odwołuje się do zasobów z pliku zasobów, która pasuje kultury <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> właściwości. Można jednak zmienić to zachowanie i określić danej kultury na potrzeby zasobów. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach pulpitu](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Właściwości  
 Właściwości `My.Resources` obiektu zapewniają dostęp tylko do odczytu do zasobów Twojej aplikacji. Aby dodać lub usunąć zasoby, należy użyć **projektanta projektu**. Dostęp do zasobów, o których dodane za pomocą **projektanta projektu** przy użyciu `My.Resources.` *resourceName*.  
  
 Można również dodać lub usunąć pliki zasobów, wybierając projekt w **Eksploratora rozwiązań** i klikając **Dodaj nowy element** lub **Dodaj istniejący element** z  **Projekt** menu. Dostępne zasoby dodane w ten sposób za pomocą `My.Resources.` *Nazwaplikuzasobów*`.`*resourceName*.  
  
 Każdy zasób ma nazwę, kategorii i wartość, a te ustawienia zasobów określają, jak uzyskać dostęp do zasobu pojawi się ona w `My.Resources` obiektu. Dla zasobów, które dodano w **projektanta projektu**:  
  
- Określa nazwę, nazwę właściwości,  
  
- Dane zasobu są wartości właściwości  
  
- Kategoria określa typ właściwości:  
  
|Kategoria|Typ danych właściwości|  
|---|---|  
|**Ciągi**|[Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Obrazy**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> Klasa pochodzi od <xref:System.IO.Stream> klasy, dzięki czemu może służyć za pomocą metod, które przyjmują strumieni, takich jak <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> metody.|  
|**Pliki**|-   [Ciąg](../../../visual-basic/language-reference/data-types/string-data-type.md) szukać plików tekstowych.<br />-   <xref:System.Drawing.Bitmap> w przypadku plików obrazu.<br />-   <xref:System.Drawing.Icon> Aby uzyskać pliki ikon.<br />-   <xref:System.IO.UnmanagedMemoryStream> dla plików dźwiękowych.|  
|**Inne**|Ustalany na podstawie informacji w oknie Projektant **typu** kolumny.|  
  
## <a name="classes"></a>Klasy  
 `My.Resources` Obiekt udostępnia każdego pliku zasobu jako klasę z właściwościami udostępnionych. Nazwa klasy jest taka sama jak nazwa pliku zasobu. Zgodnie z opisem w poprzedniej sekcji, zasobów w pliku zasobów są widoczne jako właściwości w klasie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Ustawia tytuł formularza do zasobu ciągu o nazwie `Form1Title` w plik zasobów aplikacji. Na przykład do pracy, aplikacja musi mieć ciągu o nazwie `Form1Title` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie ikony w postaci ikony o nazwie `Form1Icon` jest przechowywana w pliku zasobów aplikacji. Na przykład do pracy, aplikacja musi mieć ikony o nazwie `Form1Icon` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie obraz tła formularza zasób obrazu o nazwie `Form1Background`, która znajduje się w pliku zasobów aplikacji. W tym przykładzie do pracy, aplikacja musi mieć zasób obrazu o nazwie `Form1Background` w pliku zasobów.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odtwarza dźwięk, który jest przechowywany jako audio zasób o nazwie `Form1Greeting` pliku zasobów. Na przykład do pracy, aplikacja musi mieć audio zasób o nazwie `Form1Greeting` w pliku zasobów. `My.Computer.Audio.Play` Metoda jest dostępna tylko dla aplikacji Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pobiera kultury francuski wersję zasobu ciągu w aplikacji. Zasób o nazwie `Message`. Aby zmienić kulturę, `My.Resources` używa obiektu, w przykładzie użyto <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 W tym przykładzie do pracy, aplikacja musi mieć ciągu o nazwie `Message` w jego zasobów plików i aplikacji powinny mieć kultury francuski wersję tego pliku zasobów, Resources.fr-FR.resx. Jeśli aplikacja nie ma wersji pliku zasobów kultury francuski `My.Resource` obiektu pobiera zasób z pliku zasobów kultury domyślnej.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Zasoby w aplikacjach klasycznych](../../../framework/resources/index.md)
