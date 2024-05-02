    matchIndex = np.argmin(faceDis)

    if matches[matchIndex]:
        face_rect = haar_cascade.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=3)

        id = studentIDs[matchIndex]
        if counter == 0:
            counter = 1
            modeType = 1
            cv.putText(imgBack,"Loading ......", (162,55+320), cv.FONT_HERSHEY_COMPLEX, 2, (0,255,0), 3)
            cv.imshow('Attendence', imgBack)
            cv.waitKey(1)
            # if cv.waitKey(1) & 0xFF==ord('d'):
            #     break

        for (x,y,w,h) in face_rect:
            cv.rectangle(img, (x,y), (x+w,y+h), (0,255,0), thickness = 2)
