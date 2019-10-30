---
title: 'Porady: odczytywanie metadanych obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: cd3b636f8f0058d4a8eacc656f95d5f46b8967e2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040754"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="99104-102">Porady: odczytywanie metadanych obrazu</span><span class="sxs-lookup"><span data-stu-id="99104-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="99104-103">Niektóre pliki obrazów zawierają metadane, które można odczytać w celu określenia funkcji obrazu.</span><span class="sxs-lookup"><span data-stu-id="99104-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="99104-104">Na przykład zdjęcie cyfrowe może zawierać metadane, które można odczytać, aby określić Marka i model aparatu używane do przechwytywania obrazu.</span><span class="sxs-lookup"><span data-stu-id="99104-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="99104-105">Za pomocą interfejsu GDI+ można odczytać istniejące metadane, a także zapisać nowe metadane w plikach obrazów.</span><span class="sxs-lookup"><span data-stu-id="99104-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="99104-106">Interfejs GDI+ przechowuje poszczególne fragmenty metadanych w obiekcie <xref:System.Drawing.Imaging.PropertyItem>.</span><span class="sxs-lookup"><span data-stu-id="99104-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="99104-107">Można odczytać właściwość <xref:System.Drawing.Image.PropertyItems%2A> obiektu <xref:System.Drawing.Image>, aby pobrać wszystkie metadane z pliku.</span><span class="sxs-lookup"><span data-stu-id="99104-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="99104-108">Właściwość <xref:System.Drawing.Image.PropertyItems%2A> zwraca tablicę obiektów <xref:System.Drawing.Imaging.PropertyItem>.</span><span class="sxs-lookup"><span data-stu-id="99104-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="99104-109">Obiekt <xref:System.Drawing.Imaging.PropertyItem> ma cztery następujące właściwości: `Id`, `Value`, `Len`i `Type`.</span><span class="sxs-lookup"><span data-stu-id="99104-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="99104-110">#C1</span><span class="sxs-lookup"><span data-stu-id="99104-110">Id</span></span>

<span data-ttu-id="99104-111">Tag, który identyfikuje element metadanych.</span><span class="sxs-lookup"><span data-stu-id="99104-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="99104-112">Niektóre wartości, które można przypisać do <xref:System.Drawing.Imaging.PropertyItem.Id%2A> są przedstawione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="99104-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="99104-113">Wartość szesnastkowa</span><span class="sxs-lookup"><span data-stu-id="99104-113">Hexadecimal value</span></span>|<span data-ttu-id="99104-114">Opis</span><span class="sxs-lookup"><span data-stu-id="99104-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="99104-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="99104-115">0x0320</span></span><br /><br /> <span data-ttu-id="99104-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="99104-116">0x010F</span></span><br /><br /> <span data-ttu-id="99104-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="99104-117">0x0110</span></span><br /><br /> <span data-ttu-id="99104-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="99104-118">0x9003</span></span><br /><br /> <span data-ttu-id="99104-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="99104-119">0x829A</span></span><br /><br /> <span data-ttu-id="99104-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="99104-120">0x5090</span></span><br /><br /> <span data-ttu-id="99104-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="99104-121">0x5091</span></span>|<span data-ttu-id="99104-122">Tytuł obrazu</span><span class="sxs-lookup"><span data-stu-id="99104-122">Image title</span></span><br /><br /> <span data-ttu-id="99104-123">Producent sprzętu</span><span class="sxs-lookup"><span data-stu-id="99104-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="99104-124">Model sprzętu</span><span class="sxs-lookup"><span data-stu-id="99104-124">Equipment model</span></span><br /><br /> <span data-ttu-id="99104-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="99104-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="99104-126">Czas ekspozycji EXIF</span><span class="sxs-lookup"><span data-stu-id="99104-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="99104-127">Tabela luminancji</span><span class="sxs-lookup"><span data-stu-id="99104-127">Luminance table</span></span><br /><br /> <span data-ttu-id="99104-128">Tabela chrominance</span><span class="sxs-lookup"><span data-stu-id="99104-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="99104-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="99104-129">Value</span></span>

<span data-ttu-id="99104-130">Tablica wartości.</span><span class="sxs-lookup"><span data-stu-id="99104-130">An array of values.</span></span> <span data-ttu-id="99104-131">Format wartości jest określany przez właściwość <xref:System.Drawing.Imaging.PropertyItem.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="99104-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="99104-132">Funkcja</span><span class="sxs-lookup"><span data-stu-id="99104-132">Len</span></span>

<span data-ttu-id="99104-133">Długość (w bajtach) tablicy wartości wskazywanej przez właściwość <xref:System.Drawing.Imaging.PropertyItem.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="99104-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="99104-134">Typ</span><span class="sxs-lookup"><span data-stu-id="99104-134">Type</span></span>

<span data-ttu-id="99104-135">Typ danych wartości w tablicy wskazywanej przez właściwość `Value`.</span><span class="sxs-lookup"><span data-stu-id="99104-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="99104-136">Formaty wskazywane przez wartości właściwości `Type` są przedstawione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="99104-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="99104-137">Wartość liczbowa</span><span class="sxs-lookup"><span data-stu-id="99104-137">Numeric value</span></span>|<span data-ttu-id="99104-138">Opis</span><span class="sxs-lookup"><span data-stu-id="99104-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="99104-139">1</span><span class="sxs-lookup"><span data-stu-id="99104-139">1</span></span>|<span data-ttu-id="99104-140">`Byte`</span><span class="sxs-lookup"><span data-stu-id="99104-140">A `Byte`</span></span>|
|<span data-ttu-id="99104-141">2</span><span class="sxs-lookup"><span data-stu-id="99104-141">2</span></span>|<span data-ttu-id="99104-142">Tablica obiektów `Byte` zakodowanych jako ASCII</span><span class="sxs-lookup"><span data-stu-id="99104-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="99104-143">3</span><span class="sxs-lookup"><span data-stu-id="99104-143">3</span></span>|<span data-ttu-id="99104-144">16-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="99104-144">A 16-bit integer</span></span>|
|<span data-ttu-id="99104-145">4</span><span class="sxs-lookup"><span data-stu-id="99104-145">4</span></span>|<span data-ttu-id="99104-146">32-bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="99104-146">A 32-bit integer</span></span>|
|<span data-ttu-id="99104-147">5</span><span class="sxs-lookup"><span data-stu-id="99104-147">5</span></span>|<span data-ttu-id="99104-148">Tablica dwóch `Byte` obiektów, które reprezentują liczbę wymierną</span><span class="sxs-lookup"><span data-stu-id="99104-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="99104-149">6</span><span class="sxs-lookup"><span data-stu-id="99104-149">6</span></span>|<span data-ttu-id="99104-150">Nieużywane</span><span class="sxs-lookup"><span data-stu-id="99104-150">Not used</span></span>|
|<span data-ttu-id="99104-151">7</span><span class="sxs-lookup"><span data-stu-id="99104-151">7</span></span>|<span data-ttu-id="99104-152">definicji</span><span class="sxs-lookup"><span data-stu-id="99104-152">Undefined</span></span>|
|<span data-ttu-id="99104-153">8</span><span class="sxs-lookup"><span data-stu-id="99104-153">8</span></span>|<span data-ttu-id="99104-154">Nieużywane</span><span class="sxs-lookup"><span data-stu-id="99104-154">Not used</span></span>|
|<span data-ttu-id="99104-155">9</span><span class="sxs-lookup"><span data-stu-id="99104-155">9</span></span>|`SLong`|
|<span data-ttu-id="99104-156">10</span><span class="sxs-lookup"><span data-stu-id="99104-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="99104-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="99104-157">Example</span></span>
  
<span data-ttu-id="99104-158">Poniższy przykład kodu odczytuje i wyświetla siedem fragmentów metadanych w pliku `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="99104-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="99104-159">Drugi element właściwości (index 1) na liście ma <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (producent sprzętu) i <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tablica bajtowa zakodowana w formacie ASCII).</span><span class="sxs-lookup"><span data-stu-id="99104-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="99104-160">W przykładzie kodu jest wyświetlana wartość tego elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="99104-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="99104-161">Kod generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="99104-161">The code produces output similar to the following:</span></span>

```output
 Property Item 0
  
 id: 0x320
  
 type: 2
 
 length: 16 bytes 
  
 Property Item 1
  
 id: 0x10f
  
 type: 2 
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a><span data-ttu-id="99104-162">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="99104-162">Compiling the Code</span></span>

<span data-ttu-id="99104-163">Poprzedni przykład jest przeznaczony do użytku z Windows Forms i wymaga `e`<xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem programu obsługi zdarzeń <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="99104-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="99104-164">Obsługuj zdarzenie <xref:System.Windows.Forms.Control.Paint> formularza i wklej ten kod do programu obsługi zdarzeń malowania.</span><span class="sxs-lookup"><span data-stu-id="99104-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="99104-165">Należy zastąpić `FakePhoto.jpg` nazwą obrazu i ścieżką prawidłową w systemie i zaimportować przestrzeń nazw `System.Drawing.Imaging`.</span><span class="sxs-lookup"><span data-stu-id="99104-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="99104-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99104-166">See also</span></span>

- [<span data-ttu-id="99104-167">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="99104-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="99104-168">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="99104-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
