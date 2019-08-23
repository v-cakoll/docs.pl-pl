---
title: 'Przewodnik: Tworzenie obiektów COM przy użyciu Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 39012ebdd8946f707fe459cb09bb2bbfc8e50088
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958266"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Przewodnik: Tworzenie obiektów COM przy użyciu Visual Basic
Podczas tworzenia nowych aplikacji lub składników najlepiej utworzyć zestawy .NET Framework. Jednak Visual Basic ułatwiają również uwidocznienie składnika .NET Framework w modelu COM. Pozwala to udostępnić nowe składniki dla wcześniejszych zestawów aplikacji, które wymagają składników COM. W tym instruktażu pokazano, jak za pomocą Visual Basic uwidocznić obiekty .NET Framework jako obiekty COM, zarówno z szablonem klasy COM, jak i bez niego.  
  
 Najprostszym sposobem uwidocznienia obiektów COM jest użycie szablonu klasy COM. Szablon klasy COM tworzy nową klasę, a następnie konfiguruje projekt w celu wygenerowania warstwy i współdziałania jako obiektu COM i zarejestrowania go w systemie operacyjnym.  
  
> [!NOTE]
> Chociaż można również uwidocznić klasę utworzoną w Visual Basic jako obiekt COM dla niezarządzanego kodu do użycia, nie jest to prawdziwy obiekt COM i nie może być używany przez Visual Basic. Aby uzyskać więcej informacji, zobacz Współdziałanie [com w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Aby utworzyć obiekt COM przy użyciu szablonu klasy COM  
  
1. Otwórz nowy projekt aplikacji systemu Windows z menu **plik** , klikając pozycję **Nowy projekt**.  
  
2. W oknie dialogowym **Nowy projekt** w polu **typy projektu** Sprawdź, czy jest wybrany system Windows. Na liście **Szablony** wybierz pozycję **Biblioteka klas** , a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.  
  
3. Wybierz pozycję **Dodaj nowy element** z menu **projekt** . **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
4. Z listy **Szablony** wybierz pozycję **Klasa com** , a następnie kliknij przycisk **Dodaj**. Visual Basic dodaje nową klasę i konfiguruje nowy projekt dla międzyoperacyjności modelu COM.  
  
5. Dodaj kod, taki jak właściwości, metody i zdarzenia, do klasy COM.  
  
6. Wybierz pozycję **kompilacja ClassLibrary1** z menu **kompilacja** . Visual Basic kompiluje zestaw i rejestruje obiekt COM w systemie operacyjnym.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Tworzenie obiektów COM bez szablonu klasy COM  
 Klasy COM można także utworzyć ręcznie zamiast używać szablonu klasy COM. Ta procedura jest pomocna podczas pracy z wiersza polecenia lub w przypadku, gdy potrzebna jest większa kontrola nad sposobem definiowania obiektów COM.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Aby skonfigurować projekt do generowania obiektu COM  
  
1. Otwórz nowy projekt aplikacji systemu Windows z menu **plik** , klikając pozycję **NewProject**.  
  
2. W oknie dialogowym **Nowy projekt** w polu **typy projektu** Sprawdź, czy jest wybrany system Windows. Na liście **Szablony** wybierz pozycję **Biblioteka klas** , a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.  
  
3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**. Zostanie wyświetlony **Projektant projektu** .  
  
4. Kliknij kartę **kompilacja** .  
  
5. Zaznacz pole wyboru **Zarejestruj dla międzyoperacyjności modelu COM** .  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Aby skonfigurować kod w klasie w celu utworzenia obiektu COM  
  
1. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **Class1. vb** , aby wyświetlić swój kod.  
  
2. Zmień nazwę klasy na `ComClass1`.  
  
3. Dodaj następujące stałe do programu `ComClass1`. Będą one przechowywać stałe unikatowe identyfikatory (GUID), które są wymagane do posiadania obiektów COM.  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. W menu **Narzędzia** kliknij polecenie **Utwórz identyfikator GUID**. W oknie dialogowym **Tworzenie identyfikatora GUID** kliknij przycisk **Format rejestru** , a następnie kliknij przycisk **Kopiuj**. Kliknij przycisk **zakończenia**.  
  
5. Zastąp ciąg pusty ciągiem `ClassId` z identyfikatorem GUID, usuwając wiodące i końcowe nawiasy klamrowe. Na przykład, jeśli identyfikator GUID podany przez Guidgen to `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , kod powinien wyglądać w następujący sposób.  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. Powtórz poprzednie kroki dla `InterfaceId` i `EventsId` stałych, jak w poniższym przykładzie.  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > Upewnij się, że identyfikatory GUID są nowe i unikatowe; w przeciwnym razie składnik COM może powodować konflikt z innymi składnikami modelu COM.  
  
7. Dodaj atrybut do `ComClass1`, określając identyfikatory GUID identyfikatora klasy, identyfikator interfejsu i identyfikator zdarzenia, jak w poniższym przykładzie: `ComClass`  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. Klasy com muszą mieć `Public Sub New()` konstruktora bez parametrów lub Klasa nie zostanie poprawnie zarejestrowana. Dodaj Konstruktor bez parametrów do klasy:  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. Dodaj właściwości, metody i zdarzenia do klasy, kończąc ją z `End Class` instrukcją. Wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** . Visual Basic kompiluje zestaw i rejestruje obiekt COM w systemie operacyjnym.  
  
    > [!NOTE]
    > Obiekty COM generowane za pomocą Visual Basic nie mogą być używane przez inne aplikacje Visual Basic, ponieważ nie są one prawdziwymi obiektami COM. Próby dodania odwołań do takich obiektów COM spowodują wystąpienie błędu. Aby uzyskać szczegółowe informacje, zobacz Współdziałanie [com w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Przewodnik: implementowanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
- [Współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Rozwiązywanie problemów związanych z współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
