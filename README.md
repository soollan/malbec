# malbec

# table - fk 제대로 잡아야함.
CREATE TABLE `wine` (
  `name` varchar(100) NOT NULL COMMENT '와인이름',
  `vintage` year NOT NULL COMMENT '생산년도',
  `drink_between_begin` year DEFAULT NULL COMMENT '시음적기 시작연도',
  `drink_between_end` year DEFAULT NULL COMMENT '시음적기 마지막연도',
  `region` varchar(45) DEFAULT NULL COMMENT '생산지역',
  `vivino` float DEFAULT NULL COMMENT '비비노점수',
  `ranking_world` tinyint DEFAULT NULL COMMENT '세계랭킹',
  `ranking_region` tinyint DEFAULT NULL COMMENT '생산지역 랭킹',
  `pairing` varchar(100) DEFAULT NULL COMMENT '추천 페어링',
  PRIMARY KEY (`name`,`vintage`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COMMENT='와인정보';

CREATE TABLE `seller` (
  `namett` varchar(100) DEFAULT NULL COMMENT '와인 이름',
  `vintagett` year DEFAULT NULL COMMENT '생산연도',
  `count` tinyint DEFAULT NULL COMMENT '수량',
  `buy_place` varchar(45) DEFAULT NULL COMMENT '구입 장소',
  `buy_price` int DEFAULT NULL COMMENT '구입 가격',
  `buy_date` date DEFAULT NULL COMMENT '구입 날짜',
  KEY `vintage_idx` (`vintagett`),
  KEY `name_idx` (`namett`),
  CONSTRAINT `name` FOREIGN KEY (`namett`) REFERENCES `wine` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COMMENT='와인셀러';

CREATE TABLE `tasting` (
  `name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '와인이름',
  `vintage` year NOT NULL COMMENT '생산연도',
  `date` date DEFAULT NULL COMMENT '날짜',
  `place` varchar(45) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '장소',
  `partner` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '같이 먹은 사람',
  `color_depth` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '색의 깊이',
  `color_hue` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '색조',
  `clarity` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '명료성',
  `aroma_intensity` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '향의 강도',
  `development` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '발전(숙성)',
  `aromas` tinytext CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci COMMENT '향',
  `dry_to_sweet` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '드라이, 스위트 정도',
  `body` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `acidity` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '산도',
  `balance` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `flavor_intensity` char(1) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '맛 강도',
  `food_pairing` varchar(45) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '곁들인 음식 ',
  `memo` varchar(45) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL COMMENT '메모',
  `rating` tinyint(1) DEFAULT NULL COMMENT '최종점수',
  PRIMARY KEY (`name`,`vintage`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COMMENT='시음';
