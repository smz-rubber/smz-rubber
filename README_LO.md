# SMZ Rubber Online — Vercel + Supabase

ຊຸດສຳລັບ Deploy ລະບົບ SMZ Rubber ໃຫ້ໃຊ້ຖານຂໍ້ມູນ PostgreSQL ຂອງ Supabase ແທນ SQLite ເພື່ອໃຫ້ຂໍ້ມູນຢູ່ຖາວອນໃນ hosting ແບບ serverless.

## ກ່ອນ Deploy
1. ໃນ Supabase ເຂົ້າ Project Settings → Database → Connection string → URI. ແນະນຳໃຊ້ connection string ຈາກ Session Pooler ຖ້າ direct connection ບໍ່ຮອງຮັບ network IPv4. ຢ່າເອົາ password ຫຼື connection string ໄປສົ່ງໃນແຊັດ.
2. ໃນ Vercel ເພີ່ມ Environment Variables ທັງ Production ແລະ Preview:
   - `DATABASE_URL` = Supabase PostgreSQL URI
   - `JWT_SECRET` = ຄ່າສຸ່ມຍາວຢ່າງໜ້ອຍ 32 ຕົວ
   - `ADMIN_USER` = `admin` (ຫຼືຊື່ອື່ນທີ່ຕ້ອງການ)
   - `ADMIN_PASSWORD` = ລະຫັດ admin ທີ່ແຂງແຮງ 12+ ຕົວ
3. ເມື່ອ API ເຮັດວຽກຄັ້ງທຳອິດ ລະບົບຈະສ້າງຕາຕະລາງ ແລະຜູ້ໃຊ້ admin ໃຫ້ໂດຍອັດຕະໂນມັດ. ຕ້ອງຕັ້ງ Environment Variables ກ່ອນເປີດ API ຄັ້ງທຳອິດ.

## ວິທີ Deploy
1. ອັບໂຫຼດໄຟລ໌ໃນ repository ນີ້ໄປ GitHub.
2. ໃນ Vercel ເລືອກ Add New → Project → Import Git Repository ແລ້ວເລືອກ repository ນີ້.
3. ຕັ້ງ Environment Variables ຕາມລາຍການຂ້າງເທິງ ແລ້ວກົດ Deploy.
4. ເປີດ `https://YOUR-PROJECT.vercel.app/api/health` ຄວນເຫັນ `{"ok":true,"service":"smz-rubber"}`.
5. ເປີດ URL ຫຼັກ, ເຂົ້າດ້ວຍ username/password ທີ່ຕັ້ງໄວ້ ແລະທົດສອບດ້ວຍຂໍ້ມູນຈຳລອງກ່ອນໃຊ້ຈິງ.

## ຄຳເຕືອນ
- ຢ່າ commit `.env`, database password, JWT secret ຫຼື admin password ໃສ່ GitHub.
- ຖ້າມີການສ້າງ admin ໄປແລ້ວ, ການປ່ຽນ `ADMIN_PASSWORD` ໃນ Vercel ຈະບໍ່ປ່ຽນ password ຂອງຜູ້ໃຊ້ເກົ່າ.
- ນີ້ແມ່ນຊຸດປັບໂຄດສຳລັບ Vercel/Supabase ແຕ່ຍັງຕ້ອງທົດສອບກັບ project ຈິງ. ກ່ອນໃຊ້ເງິນຈິງ ຄວນທົດສອບ login, ຮັບຊື້, ລາຄາ, DRC, ສະຕັອກ, ຂາຍ, ແປຮູບ, ສິດ staff/admin, ການພິມ 80mm/A4 ແລະ backup/restore.
- ການຄິດໄລ່ເງິນຮັບຊື້ຕາມກົດໃນໂຄດເດີມ: ນ້ຳຢາງສົດຄິດຕາມນ້ຳໜັກແຫ້ງ (net × DRC%), ປະເພດອື່ນຄິດຕາມນ້ຳໜັກສຸດທິ. ກະລຸນາຢືນຢັນສູດນີ້ກ່ອນບັນທຶກບິນຈິງ.
